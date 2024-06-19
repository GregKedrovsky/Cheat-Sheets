# CLI
> command line interface | commands & usage

- [Bash Scripting Tutorial](https://linuxconfig.org/bash-scripting-tutorial)
- [Linux Commands Cheat Sheet](https://www.linuxtrainingacademy.com/linux-commands-cheat-sheet/)

## Contents
- [apt](
- [arp](
- [check distro](
- [cut](
- [dd](
  - [wipe a disk](
- [find](
- [grep](
- [netstat](
- [PATH](
- [printf](
- [printf vs. echo](
- [sed](
- [showmount](
- [tar](
- [tee](
- [tr](
- [untar](

## apt

```
# [1] Update package repo
apt update

# [2] Upgrade your distro
apt full-upgrade -y

# [3] Remove obsolete packages left after the upgrade 
apt autoremove

# [4] Clear local repo of useless package files
apt autoclean

# Or do it all in one line:
apt update && apt full-upgrade -y && apt autoremove && apt autoclean
```

## arp

Running `arp` at the command line will print the arp table (shows the IPs mapped to MAC addresses).

## check distro

`lsb_release` tells you which gnu/linux distro you are using

```
lsb_release -a
```

`uname -a` tells you which linux kernel you are using

```
uname -a
```

## cut

*pending*

## dd

### wipe a disk

Fill the disk with all zeros (may take a while; it switches every bit to 0):


```
dd if=/dev/zero of=/dev/sdX bs=1M 

# replace X with the target drive letter.
```

To secure wipe, populate the entire disk with random data rather than zeros (takes longer):

```
dd if=/dev/urandom of=/dev/sdX bs=1M 

# replace X with the target drive letter.
```

Sincd `dd` does not have a verbose setting, you can get some visual feedback with this (run each in a separate term window):

```
watch vmstat -d
htop
```

## find

More details on the [find.md](find.md) page. Basic Syntax: 

```
find /path/to/search/ -name searchTerm
```

If you get a bunch of garbage on the screen, send it all to /dev/null:

```
find /path/to/search/ -name searchTerm 2>/dev/null
```

## grep

### Syntax:
```grep [options...] pattern-spec [files...]```

### Purpose:
To print lines of text from the named files that match one or more of the pattern specifications. 
- Often pipe the output to something else to do something with it. 
- `grep` is used to **extract** data. `sed` can then be used to **substitute** data.

### Main Options:
- `-E` : Match using extended regular expressions
- `-F` : Match using fixed strings (default behavior w/ no options)
- `-i` : ignore lettercase when doing pattern searching
- `-l` : List the names of the files that contain a match of the pattern instead of printing the matching lines. 

### Behavior:
Read through each file named on the command line. When a line contains a match of the pattern being searched for, print that line. 

## netstat

Print network connections, routing tables, interface statistics, masquerade connections, and multicast memberships

```
netstat -ano  # shows the active connections running on your machine
```

## PATH

```
echo $PATH             # to see your current path
PATH=$PATH:$HOME/bin   # add the home dir /bin subdir to your PATH
```

To make changes to your PATH permanent, add /paths/to/directories to your `.profile` file (read each time you login).

## printf

### Syntax
```
printf format-string [arguments...]
```

`format-string` = a string describing your desired output (best supplied as a string constant in quotes).
- This will be a mix of characters to be printed literally and *format specifications*.
- Format specifications are preceded by a percent sign (%). 
  - `%s` specifies a string
  - `%d` specifies decimal integers

`arguments` = a list of arguments like strings or variable values that will correspond to the format specificatons.
- If you have more arguments than format specifications, printf will cycle through the format specifications in the format string, reusing them in order, until finished. 

### Example:

```
printf "The first program always prints '%s, %s\!'\n" Hello world
# prints: The first program always prints 'Hello, world!'
```

## printf vs. echo

```
echo $var             # is the same as...
printf '%s\n' "$var"

echo -n $var          # is the same as...
printf '%s' "$var"
```

`printf` is better than `echo` because of portability and reliability.

You cannot use `echo` to display uncontrolled data. In other words, if you're writing a script and it is taking external input (from the user as arguments, or file names from the file system...), you cannot use `echo` to display it.

```
printf '%\n' "$var"
# this will output the content of $var followed by a newline character
# regardless of what character it may contain

printf '%\n' "$var"
# this will output the content of $var without a newline character
```

All in all, you do not know what `echo "$var"` will output unless you can make sure that `$var` does not contain backslash characters and does not start with a hyphen/dash ( - ). The POSIX specification tells us to use `printf` instead in that case. 

[source](https://unix.stackexchange.com/questions/65803/why-is-printf-better-than-echo)

## sed

Clean up carriage returns from Linux to Windows (e.g., you download and edit a script on Windows machine so you can use something like Notepad++ to edit the file and then dump it back into Linux to run it).  [source](https://www.tripwire.com/state-of-security/security-awareness/oscp-journey/|Source).

```
sed -i -e 's/\r$//' [script name]
```

## showmount

The `showmount` command shows information about an NFS server. 

### Syntax:

```
/usr/sbin/showmount -e [Target IP]
```

### Options:

|  Option  | Description |
|  `-a`            | Print all remote mounts in the format hostname:directory, where hostname is the name of the client and directory is the root of the filesystem that has been mounted. |
|  `-d`            | List directories that have been remotely mounted by clients. |
|  `-e`            | Print the list of exported filesystems. |
|  `-h`            | Provide a short help summary. |
|  `--no-headers`  | Do not print headers. |
|  `-v`            | Report the current version of the program. |

## tar

Use the following command to compress an entire directory or a single file on Linux. It’ll also compress every other directory inside a directory you specify–in other words, it works recursively.

```
tar -cvzf name-of-archive.tar.gz /path/to/directory-or-file
```
- `c` - create an archive
- `v` - verbose
- `z` - zip / gnuzip
- `f` - file (name follows)

## tee

Reads from the standard input and writes to both standard output and one or more files at the same time (takes on stream of data and "T's" is out--splits it--to two targets). 

### Syntax:

```
tee [OPTIONS] [FILE_NAMES]
```
**Options:**
- `-a (--append)` - Do not overwrite the files instead append to the given files
- `-i (--ignore-interrupts)` - Ignore interrupt signals
- `FILE_NAMES` - One or more files. Each of which the output data is written to.

### Usage:
The most basic usage of the `tee` command is to [1] display the standard output (stdout) of a program and [2] write it in a file.

```
[cli program] | tee output_file.txt
```

To strip off the color codes, pipe through sed: 

```
[cli program] | sed -r 's/\x1b\[[0-9;]*m//g' | tee output_file.txt
```
- `-r   use extended regular expressions
- `s   s/regexp/replacement/
- `\x1b  The ASCII "escape" character (octal: \033, hex: \x1B or ^[ , or in decimal: 27). Used to start a series of characters called a control sequence or escape sequence

And you could always alias that in your `.bashrc` file:

```
alias tee="sed -r 's/\x1b\[[0-9;]*m//g' | tee"
```

## tr

**Translate:** Use this to (among other things) convert lower case to upper case. Example:

```
sha256sum filename.ext | tr [:lower:] [:upper:]
```

## untar

```
tar xvzf filename
```
- `x` - extract
- `v` - verbose
- `z` - zip / gnuzip
- `f` - file (name follows)

