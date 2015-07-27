---
layout: post
title:  "moreutils: the utilities package every UNIX/Linux/Mac OS
developer should know"
date:   2015-07-27 17:04
author: Miguel Rentes
comments: true
categories:
  - UNIX
  - utilities
---

Most UNIX professionals know about the [GNU core utilities][GNUCoreUtils], from the "used-everyday" ls, cp, ln, rm, touch, tail, wc, etc., to the "not-so-used" shell commands such as tsort, tac, factor, or seq. Among the UNIX utilities available, there is one package that includes some awesome utilities that makes our life's a lot easier: the [moreutils][moreUtils] package.


* [Installing](#installing)
* [The moreutils tools](#the-moreutils-tools)
    * [chronic: *runs a command quietly unless it fails*](#chronic)
    * [combine: *combine the lines in two files using boolean operations*](#combine)
    * [errno: *look up errno names and descriptions*](#errno)
    * [ifdata: *get network interface info without parsing ifconfig output*](#ifdata)
    * [ifne: *run a program if the standard input is not empty*](#ifne)
    * [isutf8: *check if a file or standard input is utf-8*](#isutf8)
    * [lckdo: *execute a program with a lock held*](#lckdo)
    * [mispipe: *pipe two commands, returning the exit status of the first*](#mispipe)
    * [parallel: *run multiple jobs at once*](#parallel)
    * [pee: *tee standard input to pipes*](#pee)
    * [sponge: *soak up standard input and write to a file*](#sponge)
    * [ts: *timestamp standard input*](#ts)
    * [vidir: *edit a directory in your text editor*](#vidir)
    * [vipe: *insert a text editor into a pipe*](#vipe)
    * [zrun: *automatically uncompress arguments to command*](#zrun)
      
## Installing
Before describing each of the utilities included, let me tell you that this package is not exclusive for Linux systems. You can install it also under Mac OS and different UNIX flavours.

Under Mac OS, just use the following command:

```
$ brew install moreutils
```

**Note**: There is a conflict between the GNU parallel utility and the shipped parallel on the moreutils package. If you want to install GNU parallel instead of the moreutils' parallel, use the following commands:

```
$ brew install moreutils --without-parallel
$ brew install parallel
```

You can read more about it [here][parallelConflict].

Under Linux, use your favourite package manager or the command line to retrieve this package.
If you are using Arch Linux all you have to do is:

```
$ sudo pacman -S moreutils
```

Under Debian/Ubuntu/Mint a similar command is:

```
$ sudo apt-get install moreutils
```

And on RHEL, Fedora, CentOS:

```
$ sudo yum install moreutils
```

Don't forget to check your Linux distribution to know how to install this package if the above commands are not for your particular Linux distribution.

##The moreutils tools

###chronic
This tool runs a command , and arranges for its standard out and standard error to only be displayed if the command fails (exits nonzero or crashes).  If the command succeeds, any extraneous output will be hidden.

Before discovering this tool I would do something like this to hide a command output:

```
$ command >& /dev/null
```
but using chronic is so much simpler, and has the benefit that I know if the command succeeded or not, which I would not know from the line above (all output is redirected to `/dev/null`).

A common use for chronic is for running a cron job. Rather than trying to keep the command quiet, and having to deal with mails containing accidental output when it succeeds, and not verbose enough output when it fails, you can just run it verbosely always, and use chronic to hide the successful output.

```
0 1 * * * chronic backup # instead of backup >/dev/null 2>&1
```
### combine
This tool combines the lines in two files using boolean operations.

```
$ combine file1 and file2

$ combine file1 not file2

$ combine file1 or file2

$ combine file1 xor file2
```

Depending on the boolean operation specified, the contents will be combined in different ways:

* **and** Outputs lines that are in file1 if they are also present in file2.

* **not** Outputs lines that are in file1 but not in file2.

* **or**  Outputs lines that are in file1 or file2.

* **xor** Outputs lines that are in either file1 or file2, but not in both files.


The input files need not be sorted, and the lines are output in the order they occur in file1 (followed by the order they occur in file2 for the two "or" operations). This means that the operations are not commutative; "a and b" will not necessarily be the same as "b and a". To obtain commutative behavior, use the `sort` and `uniq` commands to the result, like this:

```
$ cat a
one
ten
two
three
$ cat b
ten
twelve
one
thirteen
$ combine a and b
one
ten
$ combine b and a
ten
one
$ combine a and b | sort | uniq
one
ten
$ combine b and a | sort | uniq
one
ten
```

### errno
This tool looks up errno macro names, errno codes, and the corresponding descriptions.

```
$ errno ENOENT

ENOENT 2 No such file or directory

$ errno 100

ENETDOWN 100 Network is down

$ errno -l
EPERM 1 Operation not permitted
ENOENT 2 No such file or directory
ESRCH 3 No such process
EINTR 4 Interrupted system call
EIO 5 Input/output error
ENXIO 6 No such device or address
E2BIG 7 Argument list too long
ENOEXEC 8 Exec format error
EBADF 9 Bad file descriptor
ECHILD 10 No child processes
EAGAIN 11 Resource temporarily unavailable
ENOMEM 12 Cannot allocate memory
EACCES 13 Permission denied
EFAULT 14 Bad address
ENOTBLK 15 Block device required
EBUSY 16 Device or resource busy
EEXIST 17 File exists
EXDEV 18 Invalid cross-device link
ENODEV 19 No such device
ENOTDIR 20 Not a directory
(...)
```

This is a most valuable tool and a lot better than reading the system header files to figure out the meaning of a particular errno code. If you do a lot UNIX programming you know what I am taking about.

### ifdata
This tool can  be  used to check for the existence of a network interface, or to get information about the interface, such as its IP address, all statistics on input and output, number of packets, bytes, errors, drops, incoming and outgoing bit rate, etc.. Unlike `ifconfig` or `ip`, `ifdata` has simple to parse output that is designed to be easily used by a shell script.

```
$ ifdata -si eth0
1943188030 8648846 0 16803 0 0 0 0
$ ifdata -sip eth0
8649245
$ ifdata -so eth0
141940989 953001 0 0 0 0 0 0
$ ifdata -bips eth0
3012
$ ifdata -bops eth0
66
```
### ifne
This tool runs a program if the standard input is not empty. The name stands for "if not empty" and it simply runs the passed command to it, if it receives at least one byte in the `stdin`. You can also use the `-n` flag which causes `ifne` to reverse the operation, e.g., runs the command passed to it if the standard input is empty. Note that if the standard input is not empty, it is passed through ifne in this case. The below command line checks for `core` files on the current directory, and if found (standard inputs is not empty), sends a mail to user root alerting for this fact.

```
$ find . -name core | ifne mail -s "Core files found" root
```

### isutf8
This tool checks if a file or standard input are syntactically valid UTF-8. Input is either files named on the command line, or the standard input. Information about files with invalid UTF-8 are printed to standard output, otherwise nothing is printed.

### lckdo

**Note**: Now that package `util-linux` contains a similar command named `flock`, `lckdo` is deprecated, and  will  be  removed from some future version of moreutils.

The `flock` utility runs a program with a lock held, in order to prevent multiple processes from running in parallel. It locks from within shell scripts or from the command line. It locks a specified file or directory,  which  is  created  (assuming appropriate  permissions)  if it does not already exist.  By default, if the lock cannot be immediately acquired, `flock` waits until the lock is available. It can also lock an open file by its file descriptor number. Use it just like `nice` or `nohup`.


```
(shell1) $ flock /tmp -c cat
(shell2) $ flock -w .007 /tmp -c echo; /bin/echo $?
```
The first command sets an exclusive lock to directory /tmp and the second command will fail.

```
(shell1) $ flock -s /tmp -c cat
(shell2) $ flock -s -w .007 /tmp -c echo; /bin/echo $?
```
The first command sets a shared lock to directory /tmp and the second command will not fail. Notice that attempting to get exclusive lock with the second command would fail.


```
$ flock -x local-lock-file echo 'a b c'
```
This command grabs the exclusive lock `local-lock-file` before running `echo` with 'a b c'.

### mispipe

This command pipes two commands together like the shell does, but unlike piping in the shell, which returns the exit status of the last command; when using mispipe, the exit status of the first  command  is  returned.

**Note**:  Modern shells, like `bash` or `zsh`, offer a pipefail option, although that option does not behave the same like mispipe because it makes a failure of **any** command in the pipeline to be returned, not just the exit status of the first. This can be a better alternative to mispipe which only returns the exit status of the first command passed to it.


### parallel

This tool runs  the  specified command, passing it a single one of the specified arguments. This is repeated for each argument. Jobs may be run in parallel. The default is to run one job per CPU.

```
$ parallel sh -c "echo hi; sleep 2; echo bye" -- 1 2 3
```

The above command runs three subshells that each print a message, delay, and print another message. If  your  system has multiple CPUs, parallel will run some of the jobs in parallel, which should be clear from the order the messages are output.

```
$ parallel -j 3 ufraw -o processed -- *.NEF
```

The above command runs three ufraw processes at the same time until all of the NEF files have been processed.

```
$ parallel -j 3 -- ls df "echo hi"
```
The above command runs three independent commands (`ls`, `df` and the `echo`) in parallel.

**Note**: check the `xargs` command to also run multiple processes at a time, specifically with the `-n` and `-P` flags.

### pee
This command is similar to how `tee` uses the standard input but for pipes, hence the name. It allows redirecting output to multiple commands at once. Each command is run and fed a copy of the standard input. The output of all commands is sent to `stdout`. While this is similar to `tee`, a copy of the input is not sent to `stdout`, like  `tee`  does.  If that is desired, use `pee cat ...` instead.

```
$ cat file
5
4
3
2
1
$ cat file | pee 'sort -u > sorted' 'sort -R > unsorted'
$ cat sorted
1
2
3
4
5
$ cat unsorted
2
1
4
3
5
```

In this example, `pee` receives two commands: one for sorting the contents of the file, and another for randomly sorting the same file contents, outputting to two different files named sorted and unsorted, respectively.

### sponge
This tool reads  standard  input and writes it out to the specified file. Unlike a shell redirect, sponge soaks up all its input before writing the output file. This means that it only writes to the file once the input has been fully read. This allows constructing pipelines that read from and write to the same file, without needing to redirect the output to temporary files.

Instead of using these commands to sort a file contents:

```
$ sort filename | uniq > temp
$ mv temp filename
```

Just use:

```
$ sort filename | uniq | sponge filename
```

No need to redirecting anymore.

### ts
This tool adds a timestamp to the beginning of each line of input. This is an awesome tool that I like to use specially on a chain of commands where I can measure how long a given command is taking to complete before passing the control to the next command. It is also a great way of logging the time stamps of a programs' output.

```
$ cat script.sh
echo "The first line"
sleep 5s
echo "The last line"
$ chmod a+x script.sh
$ ./script.sh
The first line
The last line
$ ./script.sh | ts
Jul 27 15:50:42 The first line
Jul 27 15:50:47 The last line
```

One possible use of the `ts` command is to assert whenever a given machine is up and running. Restart a machine and then use `ping` with the `ts` to know exactly when that machine came up to life!

```
$ ping <IP address or hostname> | ts
Jul 27 15:53:15 PING EE.FF.GG.HH (EE.FF.GG.HH) 56(84) bytes of data.
Jul 27 15:53:15 From AA.BB.CC.DD icmp_seq=3 Destination Net Unreachable
Jul 27 15:53:18 From AA.BB.CC.DD icmp_seq=7 Destination Net Unreachable
(...)
Jul 27 15:54:08 64 bytes from EE.FF.GG.HH: icmp_seq=57 ttl=127 time=0.673 ms
```


The optional format parameter controls how the timestamp is formatted, as used by the C function `strftime`. The default format is `%b %d %H:%M:%S`. In addition to the regular `strftime` conversion specifications, `%.S` and `%.s` are like `%S` and `%s`, but provide sub-second resolution (i.e., "30.00001" and "1301682593.00001").

### vidir
This tool allows editing of the contents of a directory in a text editor (check the `$EDITOR` environment variable, because it will be used for the text editor of your choice). If no directory is specified, the current directory is edited. When editing a directory, each item in the directory will appear on its own numbered line. These numbers are how vidir keeps track of what items are changed. Delete lines to remove files from the directory, or edit filenames to rename files. You can also switch pairs of numbers to swap filenames. Note that if "-" is specified as the directory to edit, it reads a list of filenames from stdin and displays those for editing. Alternatively, a list of files can be specified on the command line.

### vipe
This tool allows you to run your editor in the middle of a unix pipeline and edit the data that is being piped between programs (once again, check the `$EDITOR` environment variable for your text editor of choice).

```
$ fortune | vipe | cowsay
 _________________________________________
/ "I am your density."                    \
|                                         |
| -- George McFly in "Back to the Future" |
| - This fortune cookie was just edited   |
\ by Miguel Rentes (in the future!)       /
 -----------------------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
```

On the above command I edited the fortune cookie before passing it to the cowsay command. This is a command that offers you great flexibility and power.

### zrun
This tool automatically decompresses arguments to command. Prefixing a shell command with `zrun` causes any compressed files that are arguments of the command to be transparently uncompressed to temp files (not pipes) and the uncompressed files fed to the command. This is a quick way to run a command that does not itself support compressed files, without manually uncompressing the files. For example, if you want to `diff` the contents of two archives without having to uncompress them first, use the following command:

```
$ zrun diff archive1.gz archive2.gz
```

This command will uncompress automatically the two .gz files and pass the contents to the diff command. Very cool.

The following compression types are supported: `gz bz2 Z xz lzma lzo`. If zrun is linked to some name beginning with z, like zprog, and the link is executed, this is equivalent to executing `zrun prog`.


That's it! Please don't forget to read the manpages for greater detail on the above commands. I hope you liked to learn about this fantastic tool package and that it motivated you to use it on your daily UNIX programming tasks! Until next time, have an awesome coding fun!


[GNUCoreUtils]: https://en.wikipedia.org/wiki/GNU_Core_Utilities
[moreUtils]: https://packages.debian.org/unstable/utils/moreutils
[parallelConflict]: http://superuser.com/questions/545889/how-can-i-install-gnu-parallel-alongside-moreutils
