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

## [find](../find.md)

Basic Syntax: 

```find /path/to/search/ -name searchTerm```

If you get a bunch of garbage on the screen, send it all to /dev/null:

```find /path/to/search/ -name searchTerm 2>/dev/null```

[[general_find | More details here.]]

----


## grep


## netstat


## PATH


## printf


## printf vs. echo


## sed


## showmount


## tar


## tee


## tr


## untar


