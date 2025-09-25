

More info on [[Shells and Command-line Interfaces]]

- To uses the command line in windows, use GitBash.
- GitBash is basically a shell that allows interact directly with your computer by pass commands directly to it (not using a GUI).
- On Mac you use a zsh.
- GitBash is like a self contain Unix environment within windows, configured to run Unix commands natively in windows.
- Commands:
	- `pwd` - Print Workin Directory; tells you your current directory/ folder, 'Print' is the way you tell the computer to display something on the screen.
	- `ls` - this command lists the contents of the folder
	- `cd` - change directory, changes the current working directory to the specified directory.
	- `cd ..` - moves you to the parent directory of your current directory,
	- `cd -` - this command moves you back to your most recent directory before your current directory.
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

