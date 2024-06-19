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


## sed


## showmount


## tar


## tee


## tr


## untar


