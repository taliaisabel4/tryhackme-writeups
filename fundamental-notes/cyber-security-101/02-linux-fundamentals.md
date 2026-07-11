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

| **Section** | **Applies To** | **Example** |
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

### Terminal Text Editors

Storing text with `ech`o and redirection (`>`, `>>`) is inefficient for multi-line files. Dedicated terminal text editors solve this.

`nano` is a simple, easy-to-learn editor. Key features include searching text, copy/paste, jumping to a line number, and showing your current line number.

`VIM` is a much more advanced editor with a steeper learning curve. It's customizable (remap keyboard shortcuts), offers syntax highlighting (popular with developers), works on nearly all terminals where Nano may not be installed, and has plenty of cheatsheets/tutorials available.

Using the `nano` command:

```
tryhackme@linux3:/tmp# nano myfile
```

### General/Useful Utilities

These utilities cover downloading, transferring, and serving files.

`wget` downloads files from the web over HTTP, as if accessing the file in a browser.

###### Provide the resource address:

```
wget https://assets.tryhackme.com/additional/linux-fundamentals/part3/myfile.txt
```

`scp` (Secure Copy) securely copies files between two computers over SSH, providing both authentication and encryptionIt can copy from your system to a remote system, or from a remote system to yours.

###### An example is shown:

```
# Local -> Remote (upload important.txt as transferred.txt)
scp important.txt ubuntu@192.168.1.30:/home/ubuntu/transferred.txt

# Remote -> Local (download documents.txt, save as notes.txt)
scp ubuntu@192.168.1.30:/home/ubuntu/documents.txt notes.txt
```

**Python3 HTTPServer**: Ubuntu ships with python3, which provides a lightweight, quick web server module. It serves files from the directory where you run it (the default port is 8000). Files can then be downloaded elsewhere with `curl` or `wget`.

###### An example is shown:

```
# Start the server (in the directory you want to serve)
python3 -m http.server
# Serving HTTP on 0.0.0.0 port 8000 (http://0.0.0.0:8000/) ...

# In a separate terminal, download a served file
wget http://MACHINE_IP:8000/file
```

> The server occupies its terminal until you cancel it with Ctrl+C, so use a second terminal for `wget`.

### Processes 101

**Processes** are the programs running on your machine, managed by the kernel. Each has a **PID** (Process ID) that increments in the order processes start.

###### Viewing processes:

- **`ps`**: Lists processes in your current user session, with status code, session, CPU time, and command name.
- **`ps aux`**: Shows all processes including those from other users and system processes not tied to a session.
- **`top`**: Real-time, continually refreshing statistics about running processes.

> To manage/kill a process, use: `kill <PID>`.

###### Signals control how cleanly the process is terminated:

| **Signal** | **Effect** |
| --- | --- |
| `SIGTERM` | Kill the process, but allow it to do cleanup first |
| `SIGKILL` | Kill immediately, no cleanup |
| `SIGSTOP` | Stop/suspend the process |

The OS uses namespaces to divide resources (CPU, RAM, priority) among processes and to isolate them for security; only processes in the same namespace can see each other. The process with PID 0 starts at boot — the system's init, which sits between the OS and the user. Programs you launch run as child processes of systemd, controlled by it but running with their own resources.

###### Starting and stopping a service and starting automatically on boot:

```
systemctl start apache2
systemctl stop myservice
systemctl enable myservice
```

Processes run in the foreground or background. Append `&` to run a command in the background (it returns the process ID instead of output), useful for long tasks like copying files while you keep working. Press Ctrl+Z to suspend/background a running process or script. Bring a backgrounded process back with `fg`.

### Maintaining Your System: Automation

Automation lets you schedule tasks to run at set times (backups, launching programs, running commands). This is handled by the `cron` process, which you interact with through `crontabs`.

###### A crontab is a special file whose formatting cron reads and executes line by line:

| **Field** | **Meaning** |
| --- | --- |
| `MIN` | Minute to execute at |
| `HOUR` | Hour to execute at |
| `DOM` | Day of the month |
| `MON` | Month of the year |
| `DOW` | Day of the week |
| `CMD` | The command to execute |

> Use the wildcard/asterisk `*` for any field you don't care about.

### Maintaining Your System: Package Management

Developers submit software to an apt repository; if approved it becomes publicly available, reflecting the Linux's user accessibility and open-source strengths. OS vendors maintain their own repos, and you can add community/3rd-party repos to extend your OS's capabilities.

The `apt` command is part of the apt package management suite, used to manage packages/sources and install or remove software. A key benefit over installers like `dpkg`: when you update the system, added repositories are also checked for updates. Software integrity is guaranteed using the Gnu Privacy Guard (GPG) keys.

> If the developer's keys don't match what your system trusts, the software won't download.

### Maintaining Your System: Logs

Log files live in the /var/log directory and contain logging information for applications and services on your system. The OS automatically manages them through a process called **rotating**.

Logs are valuable for monitoring system health and security. Web server logs record every request, letting admins diagnose performance issues or investigate an intruder's activity. 

### Key Takeaways
