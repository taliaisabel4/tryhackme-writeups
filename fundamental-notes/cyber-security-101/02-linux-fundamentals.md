# Linux Fundamentals

*This module ...*

> Notes from the second section of TryHackMe's **Cyber Security 101** learning path.

## Linux Fundamentals Part 1

*This room covers...*

### Running Your First Few Commands

Lightweight operating systems like Ubuntu often have no GUI (desktop environment), so most interaction happens through the **Terminal**.

###### A terminal prompt looks like this:

```
tryhackme@linux1:~$ enter commands here
```

**`echo`**: Outputs any text that you provide.

**`whoami`**: Tells you which user you are currently logged in as.

###### With `echo`, a single word needs no quotes, but any string containing spaces should be wrapped in double quotes:

```
tryhackme@linux1:~$ echo Hello
Hello
tryhackme@linux1:~$ echo "Hello Friend!"
Hello Friend!
```

###### Using `whoami` to check the current username:

```
tryhackme@linux1:~$ whoami
```

### Interafcting with the Filesystem

Being able to navigate a machine without a desktop environment is important.

**`ls`**: Listing; shows the contents of the current directory.

**`cd`**: Change directory; moves you into a specified directory.

**`cat`**: Concatenate; outputs the contents of files (not just text files).

**`pwd`**: Print working directory; shows the full path of where you currently are.

###### `ls` lists the current directory's contents:

```
tryhackme@linux1:~$ ls
'Important Files' 'My Documents' Notes Pictures
```

###### `cd` changes the directory:

```
tryhackme@linux1:~$ cd Documents
tryhackme@linux1:~/Documents$ 
```

###### `cat` outputs the file contents:

```
tryhackme@linux1:~/Documents$ ls
todo.txt
tryhackme@linux1:~/Documents$ cat todo.txt
Here's something important for me to do later!
```

###### `pwd` finds your location:

```
tryhackme@linux1:~/Documents$ pwd
/home/ubuntu/Documents
```

### Searching for Files

Rather than repeatedly using `cd` and `ls` to hunt through directories, Linux lets you search the whole filesystem quickly using dedicated commands. 

**`find`**: Searches through folders (and subfolders) to locate files.

**`grep`**: Searches the contents of files for a specific value.

**`wc -l`**: Counts the number of lines/entries in a file.

###### `find` looks through every folder in the current directory:

```
tryhackme@linux1:~$ find -name passwords.txt
./folder1/passwords.txt
```
###### If you don't know the exact name, use a wildcard `*` to match by extension:

```
tryhackme@linux1:~$ find -name *.txt
./folder1/passwords.txt
./Documents/todo.txt
```

###### `grep` searches the file's contents for a specific value, such as everything a given IP address visited in a web server's access log:

```
tryhackme@linux1:~$ grep "81.143.211.90" access.log
81.143.211.90 - - [25/Mar/2021:11:17 + 0000] "GET / HTTP/1.1" 200 417 "-" "Mozilla/5.0 (Linux; Android 7.0; Moto G(4))"
```

###### `wc -l` counts the number of lines/entries in this file:

```
tryhackme@linux1:~$ wc -l access.log
244 access.log
```

### An Introduction to Shell Operators

Shell operators are a powerful way to combine and control commands.

###### Here are the four important symbols/operators:

| **Symbol/Operator** | **Description** |
| --- | ---|
| `&` | This operator allows you to run commands in the background of your terminal. |
| `&&` | This operator allows you to combine multiple commands together in one line of your terminal. |
| `>` | This operator is a redirector, meaning that we can take the output from a command and direct it elsewhere. |
| `>>` | This operator does the same function of the `>` operator but appends the output rather than replacing. |

### Key Takeaways

## Linux Fundamentals Part 2

*This room covers...*

### Introduction to Flags and Switches

Most commands accept **arguments**, which are extra keywords supplied to change how a command behaves. These are identified by a hyphen followed by a keyword, and are known as **flags** or **switches**. Without any flags, a command performs its default behaviour; flags extend that behaviour.

`l`s lists the contents of the working directory but hides files/folders that begin with a dot (.). Adding the `-a` flag reveals the hidden folder(s).

###### The commands `ls` and `ls -a` is shown:

```
tryhackme@linux2:~$ ls
folder1
tryhackme@linux2:~$ ls -a
.hiddenfolder folder1
```

> The `-a` command is the same as using the `-all` command.

Commands that accept arguments also support a `--help` option, which lists the possible options with brief descriptions and examples.

###### The command `--help` is shown:

```
tryhackme@linux2:~$ ls --help
```

#### The Manual Page

The manual pages are a great source of information for both system commands and applications available on both a Linux machine, which is accessible on the machine itself and online.

###### Access it with the `man` command followed by the command name:

```
tryhackme@linux2:~$ man ls
```

> Inside a man page, navigate down with the down arrow key, and use the `-h` flag (with many commands) to display sizes in a human-readable format.

### Filesystem Interaction

The filesystem to allow us to create, move, and delete files and folders.

###### The filesystem commands:

| **Command** | **Full Name** | **Purpose** |
| --- | --- | --- |
| `touch` | touch | Create a blank file |
| `mkdir` | make directory | Create a folder |
| `cp` | copy | Copy a file or folder |
| `mv` | move | Move or rename a file or folder |
| `rm` | remove | Remove a file or folder |
| `file` | file | Determine the type of a file |

### Permissions 101

Certain users cannot access certain files or folders.

Running `ls -l` (or `ls -lh` for human-readable sizes) shows ten columns, but the first three are key for permissions and ownership

###### An example of using the `ls -lh` command:

```
tryhackme@linux2:~$ ls -lh
-rw-r--r-- 1 cmnatic cmnatic 0 Feb 19 10:37 file1
-rw-r--r-- 8 cmnatic cmnatic 0 Feb 19 10:37 file2
```

> Every file/folder has three permission types: Read, Write, and Execute.

#### Users vs. Groups

Linux permissions are granular. A user may own a file, but a group of users can be granted the same or different permissions to that same file without affecting the owner. Real-world example: a web server's system user needs read/write access to serve an application, while a hosting company lets customers upload their own website files without becoming that system user (which would compromise security for everyone).

Switching between users (`su`), unless you're root (or using `sudo`), you need the target username and their password.

###### Examples using the `su` and `su -l` commands:

```
tryhackme@linux2:~$ su user2
Password:
```

```
tryhackme@linux2:~$ su -l user2
Password:
user2@linux2:~$
```

> The `-l` or `--login` switch starts a shell more like a real login, inheriting the new user's environment variables and dropping you into their home directory.

#### File Permissions in Numeric Format

In Linux, every file and directory has a set of permissions that control who can read, write, or execute it.

These permissions are often displayed in symbolic format, such as: `rwxrwxrwx`.

###### This format is split into three groups:

| Section | Applies To | Example |
| --- | --- | --- |
| First 3 | Owner | `rwx` |
| Next 3 | Group | `rwx` |
| Last 3 | Others | `rwx` |

###### Each letter represents a specific permission:

- **`r`**: Read
- **`w`**: Write
- **`x`**: Execute

###### By converting symbolic permissions to numbers, each permission has a value:

| Permission | Value |
| --- | --- |
| Read (`r`) | 4 |
| Write (`w`) | 2 |
| Execute (`x`) | 1 |

###### Some common examples:

- `rwxrwxrwx` = 777
- `rwxr-xr-x` = 755
- `rw-r--r--` = 644
- `rwx------` = 700

> Numeric permissions matter because many commands use them and they help you spot security risks and control access to sensitive files.

### Common Directories

There are many common directories such as `/etc`, `/var`, `/root`, and `/tmp`.

###### The common directories are shown:

| Directory | Short For | Purpose |
| --- | --- | --- |
| `/etc` | etcetera | System configuration files used by the OS |
| `/var` | variable data | Frequently changing data (logs, databases) |
| `/root` | root | Home directory of the root user |
| `/tmp` | temporary | Volatile short-term storage, cleared on reboot |

> `/etc` is one of the most important root directories on your system.

### Key Takeaways

## Linux Fundamentals Part 3

*This room covers...*

### Key Takeaways
