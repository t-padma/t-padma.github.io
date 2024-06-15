---
layout: article
title: Git Bash
mathjax: true
tags: intro git
---

The blog's primary objective is to provide a big picture of what Git Bash is, its importance, and how it is used on a Windows Operating System. Software Carpentry's course ["The Unix Shell"](https://swcarpentry.github.io/shell-novice/01-intro.html)[^1] is the primary reference for the blog. The necessary download instructions are given in [this link](https://carpentries.github.io/workshop-template/install_instructions/#shell) under the title "The Bash Shell". Following these instructions on a Windows computer will download Git BASH, Git GUI, and Git CMD. An alternative to Git BASH is the [Windows Subsystem for Linux (WSL2)](https://learn.microsoft.com/en-us/windows/wsl/about).

**Shell** is a program that allows us to communicate with the computer using text-based commands. Shell is also called a **Terminal** or **Command-line**. The Unix shell is a shell that is both a **command-line interface** and a scripting language. Note  that Unix is different from the Unix shell. Unix is an operating system, just like Windows and Macintosh. Bash, the most popular Unix shell, is the default shell on most Unix operating systems. However, the Unix shell is not the default shell on a Windows system. Windows users instead use Git BASH, a software that provides a Bash-like interface when interacting with Git. 
Although a Graphical User Interface (GUI) is easier to use, a Command-line Interface is more convenient to work with when we want to automate several tasks.

Note that most resources[^2][^3][^4] that I came across, focus on the Unix shell, which is compatible with a Mac or Linux OS. Moreover, learning Unix shell basics is important when working with Neuroimaging Software like AFNI and FSL. The blog provides an overview of Unix Shell basics. 

### Example:
![terminal](/images/terminal.png)

The Git BASH terminal allows us to communicate with the computer using text that has a few major components. 

To begin with, when the shell is first opened, we will observe a **prompt** or `$`, indicating that the shell is waiting for input. A text cursor follows the prompt which indicates where our typing will appear. 

In the example above, `ls` is the **command**, `-F` is the option, and `"./Desktop"` is called the argument. 

```
ls -F "./Desktop"
```
The command `ls` lists the contents of the directory of interest. 

The option `-F` makes the listed output more comprehensible. Finally, the argument `"./Desktop"` specifies that the command needs to act on the Desktop directory present in the current working directory. 

Note that `.` is a short-hand to denote the current working directory.

A few important points:
1. Options change the behavior of commands.
2. Arguments tell the command what (e.g. specific file or directory) to operate on.
3. A command doesn't always require options and arguments. Moreover, commands can be called with multiple options and arguments. Therefore, options and arguments are also called **parameters**.

### Useful shortcuts
- `./` denotes the current working directory while `~` denotes the home directory.
- `../` goes a step back w.r.t the current working directory.
- Commands followed by one dash, e.g. `ls -F`, are called short options. On the other hand, commands followed by two dashes, e.g. `ls --help`, are called long options.
- `cd -` and `cd ..` are shortcuts to move back and forth between two directories.
- Commands are case-sensitive. For instance, `ls -s` is a different command from `ls -S`.
- Path to a file or directory is always provided in quotes. E.g. `ls -F "./dir1/subdir"`
- A command (with/without options) followed by no arguments implements the command in the current working directory.
- Wildcards like `*` and `?` represent character(s). `*` can stand for represents zero or more characters while `?` represents exactly one character. The example below explains the use of `*` and `?`. 

```
$ ls
cubane.pdb  ethane.pdb  methane.pdb  octane.pdb  pentane.pdb  propane.pdb

$ ls *.pdb
cubane.pdb  ethane.pdb  methane.pdb  octane.pdb  pentane.pdb  propane.pdb

$ ls *eth*
ethane.pdb  methane.pdb

$ ls ?ropane.pdb
propane.pdb

$ ls ???ane.pdb
cubane.pdb  ethane.pdb  octane.pdb
```

### Multiple options for a given command
Consider the following example:
```
ls -h -l
```
The option `-h` ensures that the output is "human readable" while the option `-l` provides a long list format. In other words, the long list provides information like file size, time last modified, etc in addition to the file/directory name.

Often, multiple options like the one above can be combined with a single dash and no spaces as follows:
```
ls -hl
```

The table below provides a brief description of different commands. To look at the available options use the `help` option. 

For example, to understand the options available for `ls`, use the command `ls --help`. Note that this option might not work for built-in commands. In such cases, try `help xxx` to get a description for the command `xxx`.

| Command | Description |
| --- | --- |
| `ls` <br> `ls "./path1" "./path2"`| List contents in the current working directory. <br> `ls` can be be given multiple paths|
| `cd` | change current working directory  |
| `pwd` |  print working directory  |
| `clear` | To clear the terminal when screen gets too cluttered. |
| `mkdir`<br> `mkdir -p "./dir/sub-dir/subsub-dir"` <br> `mkdir dir1 dir2`| To make a new directory. <br> Use option `-p` to create nested directories <br> Creates new directories called `dir1` and `dir2` in current working directory. |
|`rm` <br> `rm -i` <br> `rm -r`| to remove files. <br> The `-i` option will prompt before (every) removal. Useful since files can be deleted permanently. <br> To remove a directory and all its contents|
|`touch draft.txt`| to create a new text file called `draft` in the current working directory. |
|`mv`<br> `mv "./dir/abc.txt" "./dir/xyz.txt"` <br> `mv "./dir/abc.txt" "./dir2/subdir/abc.txt"` | to move or rename files/directories. <br> Rename the file `abc.txt` in `dir` as `xyz.txt`.<br> Move the file `abc.txt` in `dir1` to new location i.e. in `./dir2/subdir`.|
| `cp` <br> `cp -r` <br> `cp "./dir/some.dat" "./dir2/other.dat" ".\new-dir"`| To copy files. <br> To copy a directory and all its contents <br> `cp` can copy multiple files to `new-dir` |
  










[^1]: Gabriel A. Devenyi (Ed.), Gerard Capes (Ed.), Colin Morris (Ed.), Will Pitchers (Ed.), Greg Wilson, Gerard Capes, Gabriel A. Devenyi, Christina Koch, Raniere Silva, Ashwin Srinath, … Vikram Chhatre. (2019, July). swcarpentry/shell-novice: Software Carpentry: the UNIX shell, June 2019 (Version v2019.06.1). Zenodo. http://doi.org/10.5281/zenodo.3266823
[^2]: [Unix Tutorial](https://afni.nimh.nih.gov/pub/dist/doc/htmldoc/background_install/unix_tutorial/index.html) provided by AFNI.
[^3]: [Unix for Neuroimagers](https://andysbrainbook.readthedocs.io/en/latest/unix/Unix_Intro.html), Andy's Brain Book.
[^4]: [A Basic UNIX tutorial](https://fsl.fmrib.ox.ac.uk/fslcourse/unix_intro/), part of the FSL course taught at Idaho State University.
[^5]: [Creating and highlighting code blocks](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-and-highlighting-code-blocks)

