# Linux Fundamentals

*This module builds from the first commands and filesystem navigation, through flags, permissions, and system directories, and finishes with text editors, processes, and the automation, packages, and logs that keep a system running.*

[Linux Fundamentals 1](#-linux-fundamentals-1) · [Linux Fundamentals 2](#-linux-fundamentals-2) · [Linux Fundamentals 3](#-linux-fundamentals-3)

> Notes from the second section of TryHackMe's **Cyber Security 101** learning path.

## <img src="https://github.com/user-attachments/assets/705adee7-47f3-4434-b04b-c6c9b14add54" width="50" height="50" align="middle" alt="Linux Fundamentals Part 1 room icon"> Linux Fundamentals 1

*This room covers the terminal, the first essential commands, searching the filesystem, and shell operators.*

### Running Your First Few Commands

Lightweight operating systems like Ubuntu often have no GUI (desktop environment), so most interaction happens through the **Terminal**.

###### A terminal prompt looks like this:

```console
tryhackme@linux1:~$ enter commands here
```

**`echo`**: Outputs any text that you provide.

**`whoami`**: Tells you which user you are currently logged in as.

###### With `echo`, a single word needs no quotes, but any string containing spaces should be wrapped in double quotes:

```console
tryhackme@linux1:~$ echo Hello
Hello
tryhackme@linux1:~$ echo "Hello Friend!"
Hello Friend!
```

###### Using `whoami` to check the current username:

```console
tryhackme@linux1:~$ whoami
```

### Interacting with the Filesystem

Being able to navigate a machine without a desktop environment is important.

**`ls`**: Listing; shows the contents of the current directory.

**`cd`**: Change directory; moves you into a specified directory.

**`cat`**: Concatenate; outputs the contents of files (not just text files).

**`pwd`**: Print working directory; shows the full path of where you currently are.

###### `ls` lists the current directory's contents:

```console
tryhackme@linux1:~$ ls
'Important Files' 'My Documents' Notes Pictures
```

###### `cd` changes the directory:

```console
tryhackme@linux1:~$ cd Documents
tryhackme@linux1:~/Documents$
```

###### `cat` outputs the file contents:

```console
tryhackme@linux1:~/Documents$ ls
todo.txt
tryhackme@linux1:~/Documents$ cat todo.txt
Here's something important for me to do later!
```

###### `pwd` finds your location:

```console
tryhackme@linux1:~/Documents$ pwd
/home/ubuntu/Documents
```

### Searching for Files

Rather than repeatedly using `cd` and `ls` to hunt through directories, Linux lets you search the whole filesystem quickly using dedicated commands.

**`find`**: Searches through folders (and subfolders) to locate files.

**`grep`**: Searches the contents of files for a specific value.

**`wc -l`**: Counts the number of lines/entries in a file.

###### `find` looks through every folder in the current directory:

```console
tryhackme@linux1:~$ find -name passwords.txt
./folder1/passwords.txt
```
###### If you don't know the exact name, use a wildcard `*` to match by extension:

```console
tryhackme@linux1:~$ find -name *.txt
./folder1/passwords.txt
./Documents/todo.txt
```

###### `grep` searches the file's contents for a specific value, such as everything a given IP address visited in a web server's access log:

```console
tryhackme@linux1:~$ grep "81.143.211.90" access.log
81.143.211.90 - - [25/Mar/2021:11:17 + 0000] "GET / HTTP/1.1" 200 417 "-" "Mozilla/5.0 (Linux; Android 7.0; Moto G(4))"
```

###### `wc -l` counts the number of lines/entries in this file:

```console
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

Linux systems are often managed entirely from the terminal, with no graphical desktop available. A small set of commands covers most navigation and inspection needs, including `ls`, `cd`, `cat`, and `pwd` for moving around and reading files, and `find`, `grep`, and `wc -l` for locating files and searching their contents. Shell operators like `&&`, `>`, and `>>` chain commands together and redirect their output, turning individual commands into more useful workflows.

## <img src="https://github.com/user-attachments/assets/a454ca29-dd2e-435d-8c54-e746534f9a79" width="50" height="50" align="middle" alt="Linux Fundamentals Part 2 room icon"> Linux Fundamentals 2

*This room covers flags and manual pages, filesystem manipulation, permissions and user switching, and the common system directories.*

### Introduction to Flags and Switches

Most commands accept **arguments**, which are extra keywords supplied to change how a command behaves. These are identified by a hyphen followed by a keyword, and are known as **flags** or **switches**. Without any flags, a command performs its default behavior; flags extend that behavior.

`ls` lists the contents of the working directory but hides files/folders that begin with a dot (.). Adding the `-a` flag reveals the hidden folder(s).

###### The commands `ls` and `ls -a` are shown:

```console
tryhackme@linux2:~$ ls
folder1
tryhackme@linux2:~$ ls -a
.hiddenfolder folder1
```

> The `-a` flag is the same as using the `--all` flag.

Commands that accept arguments also support a `--help` option, which lists the possible options with brief descriptions and examples.

###### The command `--help` is shown:

```console
tryhackme@linux2:~$ ls --help
```

#### The Manual Page

The manual pages are a great source of information for both system commands and applications available on both a Linux machine, which is accessible on the machine itself and online.

###### Access it with the `man` command followed by the command name:

```console
tryhackme@linux2:~$ man ls
```

### Filesystem Interaction

The filesystem allows us to create, move, and delete files and folders.

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

```console
tryhackme@linux2:~$ ls -lh
-rw-r--r-- 1 cmnatic cmnatic 0 Feb 19 10:37 file1
-rw-r--r-- 8 cmnatic cmnatic 0 Feb 19 10:37 file2
```

> Every file/folder has three permission types: Read, Write, and Execute.

#### Users vs. Groups

Linux permissions are granular. A user may own a file, but a group of users can be granted the same or different permissions to that same file without affecting the owner. Real-world example: a web server's system user needs read/write access to serve an application, while a hosting company lets customers upload their own website files without becoming that system user (which would compromise security for everyone).

Switching between users (`su`), unless you're root (or using `sudo`), you need the target username and their password.

###### Examples using the `su` and `su -l` commands:

```console
tryhackme@linux2:~$ su user2
Password:
```

```console
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

Flags extend a command's default behavior, and `--help` and `ma`n make any unfamiliar command self-documenting. Linux permissions are granular, controlling read, write, and execute access separately for the owner, the group, and everyone else, which lets multiple users share a system without granting each other more access than they need. Knowing the purpose of directories like `/etc`, `/var`, `/root`, and `/tmp` tells you where configuration lives, where logs accumulate, and where an attacker might look first.

## <img src="https://github.com/user-attachments/assets/69b3fdb6-b245-4cd1-8149-7b4122a6ec60" width="50" height="50" align="middle" alt="Linux Fundamentals Part 3 room icon"> Linux Fundamentals 3

*This room covers terminal text editors, file transfer utilities, process management, and maintaining a system through automation, packages, and logs.*

### Terminal Text Editors

Storing text with `echo` and redirection (`>`, `>>`) is inefficient for multi-line files. Dedicated terminal text editors solve this.

`nano` is a simple, easy-to-learn editor. Key features include searching text, copy/paste, jumping to a line number, and showing your current line number.

`VIM` is a much more advanced editor with a steeper learning curve. It's customizable (remap keyboard shortcuts), offers syntax highlighting (popular with developers), works on nearly all terminals where Nano may not be installed, and has plenty of cheatsheets/tutorials available.

Using the `nano` command:

```console
tryhackme@linux3:/tmp# nano myfile
```

### General/Useful Utilities

These utilities cover downloading, transferring, and serving files.

`wget` downloads files from the web over HTTP, as if accessing the file in a browser.

###### Provide the resource address:

```bash
wget https://assets.tryhackme.com/additional/linux-fundamentals/part3/myfile.txt
```

`scp` (Secure Copy) securely copies files between two computers over SSH, providing both authentication and encryption. It can copy from your system to a remote system, or from a remote system to yours.

###### An example is shown:

```bash
# Local -> Remote (upload important.txt as transferred.txt)
scp important.txt ubuntu@192.168.1.30:/home/ubuntu/transferred.txt

# Remote -> Local (download documents.txt, save as notes.txt)
scp ubuntu@192.168.1.30:/home/ubuntu/documents.txt notes.txt
```

**Python3 HTTPServer**: Ubuntu ships with python3, which provides a lightweight, quick web server module. It serves files from the directory where you run it (the default port is 8000). Files can then be downloaded elsewhere with `curl` or `wget`.

###### An example is shown:

```bash
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

The OS uses namespaces to divide resources (CPU, RAM, priority) among processes and to isolate them for security; only processes in the same namespace can see each other. The process with PID 1 starts at boot. This is the system's init, which sits between the OS and the user. Programs you launch run as child processes of systemd, controlled by it but running with their own resources.

###### Starting and stopping a service and starting automatically on boot:

```bash
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

Terminal editors like `nano` and `VIM` make it practical to work with files directly on a remote machine, while `wget`, `scp`, and a quick Python HTTP server move files between systems. Processes are managed through the kernel and identified by PID, and tools like `ps`, `top`, and `kill` show what is running and stop it cleanly or forcefully. Routine maintenance rests on cron for scheduled tasks, `apt` for verified software installation, and the logs in `/var/log`, which record the activity an analyst relies on when investigating an intrusion.
