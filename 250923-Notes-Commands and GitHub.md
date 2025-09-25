

More info on [[Shells and Command-line Interfaces]]

- To uses the command line in windows, use GitBash.
- GitBash is basically a shell that allows interact directly with your computer by pass commands directly to it (not using a GUI).
- On Mac you use a zsh.
- GitBash is like a self contain Unix environment within windows, configured to run Unix commands natively in windows.
### Root vs. Home Directories

* **Hierarchical Structure:**
    * Computer filesystems are organized in a hierarchy, similar to a tree, with a single starting point.

* **The Root Directory (`/`) 🏛️**
    * The **root directory** is the single, top-most directory of the entire filesystem.
    * It is the ultimate parent that contains all other files and folders on the system.
    * It is accessed with the command: `cd /`

* **The Home Directory (`~`) 🏠**
    * The **home directory** is a user's personal workspace, located *inside* the root directory's structure.
    * It serves as the default starting location when a user opens a new terminal session.
    * It is accessed with the command: `cd` (with no arguments).

* **Command Summary**

    | `cd /` | Changes to the system's **root** directory. |
    | `cd` or `cd ~` | Changes to your personal **home** directory. |

### Important Commands
- **Commands to know**:
	- `pwd` - Print Workin Directory; tells you your current directory/ folder, 'Print' is the way you tell the computer to display something on the screen.
	- `ls` - this command lists the contents of the folder
	- `cd` - change directory, changes the current working directory to the specified directory.
	- `cd ..` - moves you to the parent directory of your current directory,
	- `cd -` - this command moves you back to your most recent directory before your current directory.
	- `cd` - this directory take you to you home directory
	- `mkdir` - makes a **new directory**, with the name you provide, **within your current directory; or along the path specified**
	- `mkdir -p` - (-p for parents) the addition of this flag will also allow for the creations of a new directory along the path specified, but will also create any necessary directories along the path if not already existed along the specified path.
	- `rm`: This is the standard command to **remove** (i.e., delete) files/ directory.
	- `rm -r` - removes a **specified directory and all its contents**
	- `rm -d` - removes a **specified empty directory**.
	- `-f`: This is the **force** flag. It modifies the `rm` command's behavior in three key ways:
	    
	    1. It will **ignore non-existent files**. If you try to delete a file that isn't there, `rm -f` won't produce an error.
	        
	    2. It will **never prompt for confirmation**. Even if a file is write-protected, `rm -f` will attempt to delete it without asking, "Are you sure?"
	        
	    3. It makes the command "silent" about errors related to non-existent files.
	        
	- `rm -f` combination is often used in automated scripts to ensure a cleanup step happens without pausing for user input or failing if the file was already gone.
	- **CAUTION** do not perform this operation in your root directory.
	- `touch` - the command creates a new file with name and type you specify.
### ⚠️ **WARNING** `rm -rf /`

The command `sudo rm -rf /` will **irreversibly delete your entire operating system**. It is a command you should **never** run on a live system. Understanding it is for defensive and educational purposes only.

Let's break down what `rm -rf /` means:

- **`rm`**: The remove command.
    
- **`-r`**: The **recursive** flag. This is the most critical part. It tells `rm` to delete not just a file, but an entire directory and **everything inside it**, including all subdirectories and their contents.
    
- **`-f`**: The **force** flag, which we just discussed. It makes the command silent, unstoppable, and non-interactive.
    
- **`/`**: The **root directory**. This is the top-level of the entire filesystem on a Linux or macOS system. Every file on your computer is located under `/`.
    

Putting it all together, the command `rm -rf /` means:

> "Forcibly and recursively delete everything on the entire computer, starting from the root directory, without asking for any confirmation."

#### The Built-in Safety Feature

Because this command is so catastrophic, most modern versions of `rm` have a built-in safety feature. If you were to accidentally type `sudo rm -rf /` and press Enter, the command would likely fail with a message like this:

```
rm: it is dangerous to operate recursively on '/'
rm: use --no-preserve-root to override this failsafe
```

This `--no-preserve-root` flag is a safety mechanism that forces you to explicitly state that you are aware you are about to do something irreversible.

-----


##  Initial Git Configuration

'Inspired by Aaron's notes'

Before using Git, you must configure your identity. This is a **one-time setup** on any new machine. These details are attached to every commit you make.

  * **Set Your Name:**
    ```bash
    git config --global user.name "Your Full Name"
    ```
  * **Set Your Email:**
    Use your GitHub `noreply` email to keep your personal email private.
    ```bash
    git config --global user.email "ID+username@users.noreply.github.com"
    ```
  * **Verify Configuration:**
    ```bash
    git config --global --list
    ```

-----

## GitHub Terminology

  * 📂 **Repository (Repo):** A project folder containing all your files and the complete history of changes.
  * ☁️ **Remote:** A version of your repository stored on a server (like GitHub). The default name for the main remote is **`origin`**.
  * 🍴 **Fork:** Your personal copy of someone else's repository.
  * 📥 **Clone:** Creating a local copy of a remote repository on your computer.
  * 📸 **Commit:** A snapshot of your changes at a specific point in time, identified by a descriptive message.
  * 📤 **Push:** Uploading your local commits to the remote repository.
  * 📥 **Pull:** Downloading the latest changes from the remote repository to your local copy.
  * ✨ **Merge:** Combining changes from different branches into a single branch.
  * 💬 **Pull Request (PR):** A formal request to merge changes from one branch into another, allowing for code review and discussion before the merge happens.

-----

## Authentication: HTTPS vs. SSH

Authentication proves your identity to GitHub. There are two main methods:

| Feature | HTTPS (Personal Access Token) | SSH (Key Pair) |
| :--- | :--- | :--- |
| **How it Works** | Uses a long, auto-generated token as a password. | Uses a cryptographic key pair (public/private). |
| **Setup** | Easier. You just generate a token on GitHub. | More involved. Requires generating keys and uploading the public key to GitHub. |
| **Convenience** | Less convenient. May require caching the token. | More convenient. No need to enter credentials repeatedly. |
| **Security** | Secure. | Generally considered the most secure method. |

-----

## Basic Git Workflow

This is the fundamental lifecycle for making a change and publishing it to GitHub.

1.  `git init`

      * **Action:** Initializes a new, empty Git repository in your current directory.

2.  `git add <files>`

      * **Action:** Stages your changed files, preparing them to be included in the next snapshot (commit). Use `git add .` to stage all changes.

3.  `git commit -m "<message>"`

      * **Action:** Creates the actual snapshot of your staged changes with a descriptive message explaining what you did.

4.  `git branch -M main`

      * **Action:** (Optional but good practice) Renames the default branch to `main`.

5.  `git remote add origin <your-repo-url>`

      * **Action:** Connects your local repository to the remote one on GitHub, naming it `origin`.

6.  `git push -u origin main`

      * **Action:** Pushes your committed changes from your local `main` branch up to the `origin` remote on GitHub.
      
7. **`git status`** 

	*  **Action:** Check the status of your local changes. You'll see which files are modified and untracked.

-----

## Best Practices

### Repository Organization

  * Use clear, descriptive repository names.
  * Always include a comprehensive **README.md** file explaining the project.
  * Use a **`.gitignore`** file to prevent unnecessary or sensitive files (like `.terraform` directories or secret files) from being committed.
  * Write clear, meaningful commit messages.

### Security

  * **Never** commit sensitive information (passwords, API keys, `.tfstate` files) to your repository.
  * Always review code in a Pull Request before merging it into your main branch.

-----

### 📚 Sources

[1] [GitHub Docs: Git Handbook](https://guides.github.com/introduction/git-handbook/)
[2] [Atlassian: Getting Started with Git](https://www.atlassian.com/git/tutorials/setting-up-a-repository)