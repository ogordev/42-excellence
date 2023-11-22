# print working directory
``` 
pwd
```

# list directories
```
ls
```

# LS + hidden files
```
ls -la
```

# change directory
```
cd
```

# MAN
show the manual page of a command
```
man ls
```
exit man by pressing q.


# CAT
The `cat` command in terminal is used to display the contents of a file on the terminal. It is short for "concatenate" and is one of the most frequently used commands in Linux. The `cat` command can be used to display the contents of a single file, multiple files, or to concatenate files. 

It can also be used to create new files, append content to existing files, and redirect output in the terminal or files The general syntax of the `cat` command is `cat [OPTION]... [FILE]...` where `OPTION` is a list of flags that modify the command's behavior, and `FILE` is a list of files that the command reads. Some common options include `-n` to display line numbers and `-E` to display line ends.


# LS
ls -l is used to list the contents of a directory in long format, showing permissions, ownership, size, and modification date of files and directories. If you have a different command in mind, please provide more details so that I can assist you accurately.

```
ls -l
```

# CHMOD
There are three types of permissions: read (**r**), write (**w**), and execute (**x**).

To **read** a file is to view its contents. For example, a text file must have **read** permission for someone to read the text within. If the user wants to add a sentence to that file, it needs **write** permission. The **execute**permission enables someone to run a file, such as a shell script or a binary program file.

The `chmod` command is used to change file permissions in Unix-based systems. The permissions are represented by a combination of letters and symbols, and they determine the level of access for the owner, group, and others. 

The letters "**r**", "**w**", and "**x**" represent read, write, and execute permissions, respectively. The symbols "**+**" and "**-**" are used to add or remove permissions, and "**=**" is used to set permissions. 

The `chmod` command can be used in two modes: symbolic mode and numeric mode. In symbolic mode, the permissions are represented by letters and symbols, while in numeric mode, the permissions are represented by numbers. 

The `ls -l` command is used to list files and directories, and the permissions are displayed in the first column of the output. Each set of permissions consists of three characters, representing the permissions for the owner, group, and others, respectively.



The string "drwx--xr-x" represents the file permissions for a directory when using the `ls -l`command. Here's the breakdown of what each character represents:

- **d**: Indicates that it is a directory. If it were a regular file, this position would be represented by a hyphen (-).
- **rwx**: Represents the permissions for the owner. In this case, the owner has read, write, and execute permissions.
- **--x**: Represents the permissions for the group. Here, the group has no permissions to read or write, but can execute.
- **r-x**: Represents the permissions for others (users not in the owner group). In this case, others have read and execute permissions, but no write permissions.

# find
```
find . \( -name "*~" -o -name "#*#" \) -exec rm {} \;
```

Here's what this command does:

- `find`: This command searches for files and directories in a directory hierarchy.
- `.`: This specifies the directory to start the search from (in this case, the current directory).
- `\( -name "*~" -o -name "#*#" \)`: This is the search pattern. It looks for files with a name ending in `~` or a name that starts and ends with `#`.
- `-exec rm {} \;`: This executes the `rm` command on each file found by `find`. The `{}` is a placeholder for the file name, and the `\;` indicates the end of the command.

Note that this command will permanently delete all files found by `find`, so use it with caution.


# execute a script
To make a script executable with /bin/sh.
1. you need to add a shebang line to the beginning of the exercise.

```
#!/bin/sh
```

2. you need to add the executable permission.

```
chmod +x script_name
```

# echo 
The echo command is a built-in Linux feature that prints out arguments as the standard output. echo is commonly used to display text strings or command results as messages.