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

### Key Takeaways

## Linux Fundamentals Part 3

*This room covers...*

### Key Takeaways
