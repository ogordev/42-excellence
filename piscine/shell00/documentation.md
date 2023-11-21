(ex00)

print working directory

```
asjhdja
```


``` 
pwd
```

list directories
```
ls
```

more information about the file and directories
```
ls -la
```

cd change directory
```
cd
```

show the manual page of a command
```
man ls
```
exit man by pressing q.

The `cat` command in terminal is used to display the contents of a file on the terminal. It is short for "concatenate" and is one of the most frequently used commands in Linux. The `cat` command can be used to display the contents of a single file, multiple files, or to concatenate files. 

It can also be used to create new files, append content to existing files, and redirect output in the terminal or files The general syntax of the `cat` command is `cat [OPTION]... [FILE]...` where `OPTION` is a list of flags that modify the command's behavior, and `FILE` is a list of files that the command reads. Some common options include `-n` to display line numbers and `-E` to display line ends.

```
cat Z
```


ls -l is used to list the contents of a directory in long format, showing permissions, ownership, size, and modification date of files and directories. If you have a different command in mind, please provide more details so that I can assist you accurately.

```
ls -l
```

# (chapter IV)
(exercise 01 )

To produce a file with an output similar to "-r--r-xr-x 1 XX XX 40 Jun 1 23:42 testShell00" when using the `ls -l` command, you can create a file with specific permissions and other attributes using the `touch` command followed by the `chmod` command. Here's how you can achieve this:



```
touch testShell00 # Create a new file named testShell00 

chmod 554 testShell00 # Set the permissions for the file

```


In this example, the `touch` command creates a new file, and the `chmod` command sets the permissions for the file. The permissions "554" correspond to "-r-xr-xr--", which matches the desired output format. The other attributes such as the owner, group, size, and modification date will be automatically generated based on the system's settings and the time of creation.This will result in a file with the specified permissions and other attributes, similar to the output you provided.


Now that you have done that, turn the file into 


```
tar -cf testShell00.tar testShell00

```

The command `tar -cf testShell00.tar testShell00` is used to create a new tar archive file named "testShell00.tar" containing the file "testShell00". Here's a breakdown of the command:

- `tar`: The command-line utility used to manipulate tar archives.
- `-c`: This option tells tar to create a new archive.
- `f testShell00.tar`: This specifies the name of the archive file to be created, in this case, "testShell00.tar".
- `testShell00`: This is the file to be included in the archive.

When you run this command, it will create a new tar archive file named "testShell00.tar" containing the file "testShell00". This can be useful for bundling multiple files or directories into a single archive for easier storage or transfer.If you encounter any issues with the `tar` command, it's important to ensure that you have the necessary permissions to create the archive and that the specified file "testShell00" exists in the current directory.

Don't forget to remove the testShell00 file as you only need to hand in the testShell00.tar file.


```
rm -r testShell00
```


# (chapter V)
(ex02)

Create the following files and directories. Do what’s necessary so that when you use the ls -l command in your directory, the output will looks like this :


```
|%> ls -l total XX|
drwx--xr-x 2 XX XX XX Jun 1 20:47 test0
-rwx--xr-- 1 XX XX 4 Jun 1 21:46 test1
dr-x---r-- 2 XX XX XX Jun 1 22:45 test2
-r-----r-- 2 XX XX 1 Jun 1 23:44 test3
-rw-r----x 1 XX XX 2 Jun 1 23:43 test4
-r-----r-- 2 XX XX 1 Jun 1 23:44 test5
lrwxrwxrwx 1 XX XX 5 Jun 1 22:20 test6 -> test0|
|%>|
```

I guess i need to learn more about chmod for this.

Every object on your Linux system has a permission mode that describes what actions a user can perform on it. 

There are three types of permissions: read (**r**), write (**w**), and execute (**x**).

To **read** a file is to view its contents. For example, a text file must have **read** permission for someone to read the text within. If the user wants to add a sentence to that file, it needs **write** permission. The **execute**permission enables someone to run a file, such as a shell script or a binary program file.

The `chmod` command is used to change file permissions in Unix-based systems. The permissions are represented by a combination of letters and symbols, and they determine the level of access for the owner, group, and others. 

The letters "**r**", "**w**", and "**x**" represent read, write, and execute permissions, respectively. The symbols "**+**" and "**-**" are used to add or remove permissions, and "**=**" is used to set permissions. 

The `chmod` command can be used in two modes: symbolic mode and numeric mode. In symbolic mode, the permissions are represented by letters and symbols, while in numeric mode, the permissions are represented by numbers. 

The `ls -l` command is used to list files and directories, and the permissions are displayed in the first column of the output. Each set of permissions consists of three characters, representing the permissions for the owner, group, and others, respectively.


First we need to modify the permission of test0 to:

	drwx--xr-x

The string "drwx--xr-x" represents the file permissions for a directory when using the `ls -l`command. Here's the breakdown of what each character represents:

- **d**: Indicates that it is a directory. If it were a regular file, this position would be represented by a hyphen (-).
- **rwx**: Represents the permissions for the owner. In this case, the owner has read, write, and execute permissions.
- **--x**: Represents the permissions for the group. Here, the group has no permissions to read or write, but can execute.
- **r-x**: Represents the permissions for others (users not in the owner group). In this case, others have read and execute permissions, but no write permissions.

In summary, the string "drwx--xr-x" indicates that it is a directory with specific read, write, and execute permissions for the owner, group, and others.

Thus execute this command:

```
chmod u=rwx,g=,o=rx test0
```


Looks good!

Next up, we need to achieve the following state for test1:

	-rwx--xr-- 1 XX XX 4 Jun 1 21:46 test1

*to obtain this permission level: -rwx--xr--*

ive used

```
chmod 751 test1
```

i get this output: -rwxr-x--x

thus i still need to modify some permissions.

```
chmod +xr test1
```

now verify output with

```
ls -l
```

seems correct.

resources:
man ls

https://www.pluralsight.com/blog/it-ops/linux-file-permissions

*to obtain this permission level: dr-x---r--* 

I think that I need a deeper understanding of the chmod command.
Let's do some research.

SYMBOLIC MODE
```shell
$ chmod [references][operator][modes] file ...
```

Classes of users are used to distinguish to whom the permissions apply. If no classes are specified "all" is implied. The classes are represented by one or more of the following letters:

|Reference|Class|Description|
|---|---|---|
|u|user|file owner|
|g|group|members of the file's group|
|o|others|users who are neither the file's owner nor members of the file's group|
|a|all|all three of the above, same as `ugo`|
|_(empty)_|default|same as "all", except that bits in the [umask](https://en.wikipedia.org/wiki/Umask "Umask") will be unchanged|

The chmod program uses an operator to specify how the modes of a file should be adjusted. The following operators are accepted:

|Operator|Description|
|---|---|
|+|adds the specified modes to the specified classes|
|-|removes the specified modes from the specified classes|
|=|the modes specified are to be made the exact modes for the specified classes|

The modes indicate which permissions are to be granted or removed from the specified classes. There are three basic modes which correspond to the basic permissions:

  

|Mode|Name|Description|
|---|---|---|
|r|read|**r**ead a file or list a directory's contents|
|w|write|**w**rite to a file or directory|
|x|execute|e**x**ecute a file or recurse a directory tree|
|X|special execute|which is not a permission in itself but rather can be used instead of x. It applies execute permissions to directories regardless of their current permissions and applies execute permissions to a file which already has at least one execute permission bit already set (either _User_, _Group_ or _Others_). It is only really useful when used with `+` and usually in combination with the `-R` flag for giving _Group_ or _Others_ access to a big directory tree without setting execute permission on normal files (such as text files), which would normally happen if you just used `chmod -R a+rx .`, whereas with X you can do `chmod -R a+rX .` instead|
|s|setuid/gid|Further information: [§ Special modes](https://en.wikipedia.org/wiki/Chmod#Special_modes)|
|t|sticky|Further information: [§ Special modes](https://en.wikipedia.org/wiki/Chmod#Special_modes)|

Multiple changes can be specified by separating multiple symbolic modes with commas (without spaces). If a user is not specified, `chmod` will check the [umask](https://en.wikipedia.org/wiki/Umask "Umask") and the effect will be as if "**a**" was specified except bits that are set in the umask are not affected.

Thus to remove all permissions:

```
chmod 000 filename
```

Fuck wikipedia just read the manual:

NAME
     chmod -- change file modes or Access Control Lists



SYNOPSIS
 chmod [-fv] [-R [-H | -L | -P]] mode file ...
 chmod [-fv] [-R [-H | -L | -P]] [-a | +a | =a] ACE file ...
 chmod [-fhv] [-R [-H | -L | -P]] [-E] file ...
 chmod [-fhv] [-R [-H | -L | -P]] [-C] file ...
 chmod [-fhv] [-R [-H | -L | -P]] [-N] file ...

DESCRIPTION
 The chmod utility modifies the file mode bits of the listed files as specified by the mode operand. It may also be used to modify the Access Control Lists (ACLs) associated with the listed files.
 
 The generic options are as follows:

 -f      Do not display a diagnostic message if chmod could not modify the mode for file, nor modify the exit status to reflect such failures.

 -H      If the -R option is specified, symbolic links on the command line are followed and
 hence unaffected by the command.  (Symbolic links encountered during tree traversal
 are not followed.)

 -h      If the file is a symbolic link, change the mode of the link itself rather than the
 file that the link points to.

-L      If the -R option is specified, all symbolic links are followed.

-P      If the -R option is specified, no symbolic links are followed.  This is the default.

-R      Change the modes of the file hierarchies rooted in the files, instead of just the
files themselves.  Beware of unintentionally matching the ``..'' hard link to the parent directory when using wildcards like ``.*''.

-v      Cause chmod to be verbose, showing filenames as the mode is modified.  If the -v flag
is specified more than once, the old and new modes of the file will also be printed,
in both octal and symbolic notation.

The -H, -L and -P options are ignored unless the -R option is specified.  In addition, these
options override each other and the command's actions are determined by the last one specified.

If chmod receives a SIGINFO signal (see the status argument for stty(1)), then the current
filename as well as the old and new modes are displayed.

Only the owner of a file or the super-user is permitted to change the mode of a file.

EXIT STATUS
The chmod utility exits 0 on success, and >0 if an error occurs.


MODES
Modes may be **absolute** or **symbolic**.  

An **absolute** mode is an octal number constructed from the sum of one or more of the following values:


4000    (the setuid bit).  Executable files with this bit set will run with effective
uid set to the uid of the file owner.  Directories with this bit set will force
all files and sub-directories created in them to be owned by the directory owner
and not by the uid of the creating process, if the underlying file system sup-
ports this feature: see chmod(2) and the suiddir option to mount(8).

2000    (the setgid bit).  Executable files with this bit set will run with effective
gid set to the gid of the file owner.

1000    (the sticky bit).  See chmod(2) and sticky(7).

0400    Allow read by owner.

0200    Allow write by owner.

0100    For files, allow execution by owner.  For directories, allow the owner to search
in the directory.

0040    Allow read by group members.

0020    Allow write by group members.

0010    For files, allow execution by group members.  For directories, allow group mem-
bers to search in the directory.

0004    Allow read by others.

0002    Allow write by others.

0001    For files, allow execution by others.  For directories allow others to search in
the directory.



For example, the **absolute** mode that permits read, write and execute by the owner, read and execute by group members, read and execute by others, and no set-uid or set-gid behaviour is 755 (400+200+100+040+010+004+001).



The **symbolic** mode is described by the following grammar:

	   mode         ::= clause [, clause ...]
	   clause       ::= [who ...] [action ...] action
	   action       ::= op [perm ...]
	   who          ::= a | u | g | o
	   op           ::= + | - | =
	   perm         ::= r | s | t | w | x | X | u | g | o

dr-x---r-- 2 XX XX XX Jun 1 22:45 test2


UUUGGGOOO
111 000 111 
707
chmod 707 test2


Alright now to solve the last line (test6)

For that you will need to use the ln function to create a symbolic link.

```
ln -s test0 test6
```

we have this output:

```
lrwxr-xr-x
```

However  I need the following output
```
lrwxrwxrwx
```

I thought it would be easy to fix by doing 

```
chmod 777 test6
```

Unfortunately this modified the permission of test0 not test6.
After reading the manual some more...

```
chmod -h 777 test6
```

What does the -h argument do on the chmod command?
If the file is a symbolic link, change the mode of the link itself rather than the
file that the link points to.

However I still notice some discrepancies between the required answer and my output.

I think that it's because of the -l argument of ls that I didnt understand fully.

Let's do more research.

 The Long Format
If the -l option is given, the following information is displayed for each file: file mode,
number of links, owner name, group name, number of bytes in the file, abbreviated month, day-of-month file was last modified, hour file last modified, minute file last modified, and the pathname.  

In addition, for each directory whose contents are displayed, the total number of
512-byte blocks used by the files in the directory is displayed on a line by itself, immedi-
ately before the information for the files in the directory.  If the file or directory has
extended attributes, the permissions field printed by the -l option is followed by a '@' character.  Otherwise, if the file or directory has extended security information (such as an access control list), the permissions field printed by the -l option is followed by a '+'
character.  If the -% option is given, a '%' character follows the permissions field for data-
less files and directories, possibly replacing the '@' or '+' character.

If the modification time of the file is more than 6 months in the past or future, then the
year of the last modification is displayed in place of the hour and minute fields.

If the owner or group names are not a known user or group name, or the -n option is given, the numeric ID's are displayed.

If the file is a character special or block special file, the major and minor device numbers
for the file are displayed in the size field.  If the file is a symbolic link, the pathname of
the linked-to file is preceded by ``->''.

The file mode printed under the -l option consists of the entry type, owner permissions, and group permissions.  The entry type character describes the type of file, as follows:

           b     Block special file.
           c     Character special file.
           d     Directory.
           l     Symbolic link.
           s     Socket link.
           p     FIFO.
           -     Regular file.

  The next three fields are three characters each: owner permissions, group permissions, and
The next three fields are three characters each: owner permissions, group permissions, and
other permissions.  Each field has three character positions:

1.   If r, the file is readable; if -, it is not readable.

2.   If w, the file is writable; if -, it is not writable.

3.   The first of the following that applies:

**S**     If in the owner permissions, the file is not executable and set-user-ID
mode is set.  If in the group permissions, the file is not executable
and set-group-ID mode is set.

**s**     If in the owner permissions, the file is executable and set-user-ID
mode is set.  If in the group permissions, the file is executable and
setgroup-ID mode is set.

**x**     The file is executable or the directory is searchable.

-     The file is neither readable, writable, executable, nor set-user-ID nor
set-group-ID mode, nor sticky.  (See below.)

These next two apply only to the third character in the last group (other permis-
sions).

T     The sticky bit is set (mode 1000), but not execute or search permis-
sion.  (See chmod(1) or sticky(8).)

t     The sticky bit is set (mode 1000), and is searchable or executable.
(See chmod(1) or sticky(8).)

DIAGNOSTICS
**The ls utility exits 0 on success, and >0 if an error occurs.**

MY OUTPUT RN

drwxrwxrwx  2 ijasinsk  2023_bangkok  68 Nov 20 15:32 test0
-rwxr-xr-x  1 ijasinsk  2023_bangkok   0 Nov 20 14:47 test1
dr-x---r--  2 ijasinsk  2023_bangkok  68 Nov 20 15:53 test2
-r-----r--  1 ijasinsk  2023_bangkok   0 Nov 20 14:47 test3
-rw-r----x  1 ijasinsk  2023_bangkok   0 Nov 20 14:47 test4
-rw-r--r--  1 ijasinsk  2023_bangkok   0 Nov 20 14:47 test5
lrwxrwxrwx  1 ijasinsk  2023_bangkok   5 Nov 20 16:38 test6 -> test0

WHAT MY OUTPUT SHOULD PROB LOOK LIKE

drwxrwxrwx  2 ijasinsk  2023_bangkok  0 Nov 20 15:32 test0
-rwxr-xr-x  1 ijasinsk  2023_bangkok   0 Nov 20 14:47 test1
dr-x---r--  2 ijasinsk  2023_bangkok  0 Nov 20 15:53 test2
-r-----r--  2 ijasinsk  2023_bangkok   0 Nov 20 14:47 test3
-rw-r----x  1 ijasinsk  2023_bangkok   0 Nov 20 14:47 test4
-rw-r--r--  2 ijasinsk  2023_bangkok   0 Nov 20 14:47 test5
lrwxrwxrwx  1 ijasinsk  2023_bangkok   0 Nov 20 16:38 test6 -> test0



# (chapter VI)
(ex03)

```
cp ~/.ssh/id_rsa.pub ~/dev/shell00/ex03
```


# (chapter VII)
(ex04)

```
touch midLS
```

```
nano midLS
```


In a midLS file, place the command line that will list all files and directories in your current directory (except for hidden files or any file that starts by a dot - yes, that includes double-dots), separated by a comma and a space, by order of modification date. Make sure the directory’s names are followed by a slash character.

sooo how would you construct that commad?


```
ls -A
```
List all entries except for . and ...  Always set for the super-user.


```
ls -t
```
Sort by time modified (most recently modified first) before sorting the operands by lexicographical order.


write this command inside the file:

```
ls -l -t | grep -v '^d' | awk '{print $9}' | tr '\n' ', ' | sed 's/,$//'
```

Let's break down the command:

- `ls -l -t`: Lists files and directories in long format sorted by modification time.
- `grep -v '^d'`: Excludes directories from the list.
- `awk '{print $9}'`: Selects the file/directory names from the output.
- `tr '\n' ', '`: Replaces newlines with commas and spaces.
- `sed 's/,$//'`: Removes the trailing comma at the end of the output.

When you run this command, it will list all files and directories in the current directory (excluding hidden files) by order of modification date, separated by a comma and a space.

Don't forget to make sure that Exercises in Shell must be executable with /bin/sh.

to do that you need to add a shebang line to the beginning of the exercise.

```
#!/bin/sh
```


# (chapter VIII)
(ex05)

MILESTONE!!!


# (chapter IX)
(ex06)

https://docs.github.com/en/get-started/getting-started-with-git/ignoring-files#:~:text=To%20always%20ignore%20a%20certain,config%2Fgit%2Fignore%20.
# (chapter X)
(ex07)

solved by using this
```
patch a sw.diff -o b
```



# chapter XI
(ex08)


• In a file called clean place the command line that will search for all files - in the current directory as well as in its sub-directories - with a name ending by ~, or a name that start and end by #
• The command line will show and erase all files found.
• Only one command is allowed: no ’;’ or ’&&’ or other shenanigans.


To search for all files in the current directory and its subdirectories with a name ending by ~ or a name that starts and ends by #, and then show and erase all files found, you can use the following command line in the "clean" directory:

```
find . \( -name "*~" -o -name "#*#" \) -exec rm {} \;
```

Here's what this command does:

- `find`: This command searches for files and directories in a directory hierarchy.
- `.`: This specifies the directory to start the search from (in this case, the current directory).
- `\( -name "*~" -o -name "#*#" \)`: This is the search pattern. It looks for files with a name ending in `~` or a name that starts and ends with `#`.
- `-exec rm {} \;`: This executes the `rm` command on each file found by `find`. The `{}` is a placeholder for the file name, and the `\;` indicates the end of the command.

Note that this command will permanently delete all files found by `find`, so use it with caution.

Sources
[1] Tracking down where disk space has gone on Linux? https://unix.stackexchange.com/questions/125429/tracking-down-where-disk-space-has-gone-on-linux
[2] Find a Directory/Folder with CMD without knowing full path - Super User https://superuser.com/questions/428088/find-a-directory-folder-with-cmd-without-knowing-full-path
[3] Finding and Removing Unused Files Through Command Line - Stack Overflow https://stackoverflow.com/questions/14188758/finding-and-removing-unused-files-through-command-line
[4] How to Search for Files from the Linux Command Line - freeCodeCamp https://www.freecodecamp.org/news/how-to-search-for-files-from-the-linux-command-line/
[5] Use the Unix find command to search for files - Indiana University Knowledge Base https://kb.iu.edu/d/admm



# chapter XII
(ex09)

• Create a magic file called ft_magic that will be formatted appropriately to detect files of 42 file type, built with a "42" string at the 42nd byte.

To create a magic file called "ft_magic" that can detect files of the "42" file type, built with a "42" string at the 42nd byte, you can use the following content for the "ft_magic" file:

```plaintext
0       string          42              42 file
```

This content specifies that the "42 file" type can be detected by the presence of the string "42" at the 42nd byte of the file. After creating the "ft_magic" file, you can use the `file` command to detect the "42" file type in a file by running:

```bash
file -m ft_magic <file_name>
```

Replace `<file_name>` with the name of the file you want to check. This command will use the "ft_magic" file to detect if the specified file is of the "42" file type based on the content at the 42nd byte.

For more information on the "magic" file format and its usage, you can refer to the man pages for `magic` and `file` by running `man magic` and `man file` in your terminal.

Sources
[1] magic file capable of detecting file types - Ask Ubuntu https://askubuntu.com/questions/1442599/magic-file-capable-of-detecting-file-types
[2] Create Magic File in Bash - CodePal - Code Generator https://codepal.ai/code-generator/query/RfYWDqaZ/create-magic-file-in-bash
[3] Anyone care to explain what a magic file is and what it does? : r/unix - Reddit https://www.reddit.com/r/unix/comments/x1lt4z/anyone_care_to_explain_what_a_magic_file_is_and/
[4] My file doesn't return the magic file message - Stack Overflow https://stackoverflow.com/questions/64888377/my-file-doesnt-return-the-magic-file-message
[5] Magic File Format in Linux Unix Shell Explained and Simplified - YouTube https://youtube.com/watch?v=fVOd3Dxifms


this was kinda bullshit


```
nano ft_magic

```


create test file that matches required 
```
printf '%-41s%s\n' '' '42' > example_42.txt
```

check file
```
file -m ft_magic example_42.txt
```

compile 
```
file -C -m ft_magic
```

```
pwd
```



```
export MAGIC=/Users/ijasinsk/dev/intra-uuid-a035d761-b64a-40c2-a264-0aaa94a3022d-5321057-ijasinsk/ex09/ft_magic.mgc
```

