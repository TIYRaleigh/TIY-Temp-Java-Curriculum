### Terminal

Terminal is an application included with OS X that lets us interact with our computer using a text-based interface. This may be an uncomfortable way to work at first, but it allows us to perform many tasks more efficiently.

Using the terminal can be a bit daunting at first, but it's a skill every developer should master - some things simply aren't possible using a GUI, and many tasks that are possible are still somewhat painful, whereas we can act with speed and precision by typing commands directly into the terminal.

### Starting Terminal

Terminal is tucked away under the Utilities folder in the Applications folder. You can find it in `Applications > Utilities > Terminal.app`. You can also open it by using Spotlight (`⌘-space`) and typing in `Terminal`.

This will open up a _shell_. A shell is an interface for typing commands and looking at their output. Terminal will present you with a prompt and wait for your commands. Terminal opens to a screen that looks like this:

![Screen Shot 2016-03-28 at 8.32.47 AM.png](https://tiy-learn-content.s3.amazonaws.com/67ad7971-Screen%20Shot%202016-03-28%20at%208.32.47%20AM.png)

The second line in this output should look something like `Dougs-MacBook-Pro:~ doug$`. This shows your machine name (mine is Dougs-MacBook-Pro) and your username (mine is doug). The `$` is a _prompt_. It indicates where you type commands. You press `enter` to execute the command. 

Throughout these lessons, when you see `$`, you can assume it means whatever your prompt shows you. Things after the `$` are meant to be typed as commands.

You will also see lines starting with `#` that describe what the command should do or show the expected output. For instance, take the following:

```
$ echo "Hello, Iron Yardigans"
# Hello, Iron Iron Yardigans
```

You should type `echo "Hello, Iron Yardigans"` at the prompt, press the `enter` key, and `Hello, Iron Yardigans` should appear on the line below.

Congratulations, you just ran a program from the terminal!

If you make a mistake typing a command you'll get an error message. For example:

![error in terminal.png](https://tiy-learn-content.s3.amazonaws.com/f33a5f5d-error%20in%20terminal.png)

### Command Line Syntax

When you type a command at terminal, you are first telling the terminal which program you want it to run. The program is followed by command-line _arguments_ afterward which control what the program does. Arguments are separated by spaces. Most programs cab take multiple arguments.

In the case of the `echo` example above, `echo` was the name of the program, and `"Hello, Iron Yardigans"` was an argument passed to it.

Programs run from the terminal often have multiple options for how they can run. These options are sometimes referred to as _flags_ or _switches_, and are often specified by using `-` or `--` before some letter or word.

Even a simple program like echo has an option.

```
$ echo -n "Spiffy"
# What does -n do?
```

Note that when we run the above, it doesn't print out `-n`. This is because the `echo` program treats it as an option to turn off printing a trailing newline character (that is, the equivalent of hitting return on the keyboard). Normally echo will print things on a line and finish with a newline. Using `-n` turns off the newline.

### Help!

How do we know what options we can use? Programs can have many options available to them. We don't need to memorize all of them. Most command line programs will print out some helpful information on how to use the program. The help argument is usually one of `-?`, `-h`, or `--help`. Some programs (such as `git`) will print out the help information if no arguments are provided. 

The following command will show us some of the options when using `git`:

```
Dougs-MacBook-Pro:~ doug$ git --help
usage: git [--version] [--help] [-C <path>] [-c name=value]
           [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
           [-p | --paginate | --no-pager] [--no-replace-objects] [--bare]
           [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
           <command> [<args>]

These are common Git commands used in various situations:

start a working area (see also: git help tutorial)
   clone      Clone a repository into a new directory
   init       Create an empty Git repository or reinitialize an existing one

work on the current change (see also: git help everyday)
   add        Add file contents to the index
   mv         Move or rename a file, a directory, or a symlink
   reset      Reset current HEAD to the specified state
   rm         Remove files from the working tree and from the index

examine the history and state (see also: git help revisions)
   bisect     Use binary search to find the commit that introduced a bug
   grep       Print lines matching a pattern
   log        Show commit logs
   show       Show various types of objects
   status     Show the working tree status

grow, mark and tweak your common history
   branch     List, create, or delete branches
   checkout   Switch branches or restore working tree files
   commit     Record changes to the repository
   diff       Show changes between commits, commit and working tree, etc
   merge      Join two or more development histories together
   rebase     Forward-port local commits to the updated upstream head
   tag        Create, list, delete or verify a tag object signed with GPG

collaborate (see also: git help workflows)
   fetch      Download objects and refs from another repository
   pull       Fetch from and integrate with another repository or a local branch
   push       Update remote refs along with associated objects

'git help -a' and 'git help -g' list available subcommands and some
concept guides. See 'git help <command>' or 'git help <concept>'
to read about a specific subcommand or concept.
Dougs-MacBook-Pro:~ doug$ 
```

Some commands don't have built-in help, though; `echo` is one of them. Sometimes, you need to open up a _manpage_. Manpage stands for manual page. IE: documentation. You can run the `man` command at the terminal to open up manpages:

```
$ man echo
```

One warning about manpages: they open up using a tool called `less`, which might cause you to panic a little bit, because less doesn't quit instantly like `echo` does. Don't worry! You can just press the `q` key on your keyboard to quit less when you're done reading. After you press `q`, you will be returned back to your shell.

You can use man for many commands, even ones that respond to `--help`. Manpages often contain significantly more detailed information.

### Navigation

How to get your bearings and get around in the terminal

#### Files and Directories

It's important to get familiar with some concepts that are related to the _filesystem_ of your computer. You'll have to interact with it in many ways as a developer, so let's start with some basic terminology.

A **file** is a named piece of data stored on your computer (usually on a hard disk or SSD, though not necessarily). Files can be _written to_ (saved) and _read from_ (opened).

A **directory** (or _folder_) is a container that can hold files and other directories.

You can think of directories like physical folders if you like, and files like individual documents within the folders. The analogy breaks down when you realize that you can put directories inside directories inside directories many levels deep, but it isn't a bad starting point.

Using Finder, it isn't hard to navigate the filesystem - you double-click on a folder, and it shows you the contents of the folder. We need to use commands to navigate at the command line, though.

#### Getting Your Bearings

The first part of navigating (in the real world and the virtual) is trying to figure out where we are. This is a concept known as the **working directory** - if we attempt to open a file, the operating system will first look for the file in the working directory before looking elsewhere if applicable.

The `pwd` command is used to _print_ the _working directory_.

```bash
$ pwd
# /Users/<your username>
```

If you have just opened Terminal and type `pwd`, most likely you will see `/Users/<your username>` - the default working directory when you open a new terminal window is your **home directory**. This is the directory where you can store your documents, settings, and other user-specific information.

The slashes (`/`) are called **separators** - they break apart a _path_ into the hierarchy of directories to get to the file or directory.

But wait - there's a `/` before `Users`. What's that all about?

If a path starts with a `/`, it is called an **absolute path** - that is, it starts at the **root** of the filesystem, which is indicated by a lone `/`.

So `/Users/james` means "start at the root of the filesystem, go into a directory called `Users`, and then go into a directory called `james`."

Note that for the default prompt, the current working directory (or at least a part of it) is shown before the `$`. You might see a `~` character in your prompt - this is a shortcut for _your own home directory_.

Let's look around a little bit to make some more sense of things. The `ls` command is used to _list_ the contents of the current working directory.

```bash
$ ls
# A list of your user-specific files and folders
# (Desktop, Documents, Downloads, Library, Pictures, etc.)
```

You can get even more information by using the `-la` (lowercase _ell_, not the number one!) flags with the `ls` command:

```bash
$ ls -la
# Lists all files in the current directory, with extra information shown
```

The `-l` flag tells `ls` to use the _long_ format for output. Normally, `ls` just shows the names of the files/directories. `-l` tells it to show permission, size, and the time of the last modification. The `-a` flag tells `ls` to show _all_ files, including those that would normally be hidden from view.

Now we can see some more of our surroundings! We now have a GPS (`pwd`) and a way to look at what's directly in front of us (`ls`). But what if we want to move? For that, we need to use the `cd` command to _change_ our working _directory_.

```bash
$ cd Downloads
# The prompt should change to show a new working directory
$ ls
# You should see your recently downloaded files,
# unless you've cleaned out the Downloads folder
```

We just took a step inside another directory. If we `pwd` now, we'll see that we are in `/Users/<your username>/Downloads`. You may have directories inside the `Downloads` directory - you can `cd` into these too!

But wait - how do we go back? `cd` is still used, but if you try just typing the name of the upper level directory, it won't back you out. You need to use two dots (`..`) to refer to the **parent directory** (that is, the directory that contains the current working directory).

```bash
$ cd ..
# Now you should be back in your home folder - use pwd to check
```

There are also times when you want to refer to the **current directory** - using a single dot (`.`) will let you do this. Try it with `cd`:

```bash
$ cd .
# The working directory should be exactly the same
```

### Making Changes

Any action that can be performed with Finder can be performed from the command line, sometimes more efficiently. So far we've seen how to _navigate_ around directories. We can also _make directories_ from the command line using the `mkdir` command:

```bash
$ mkdir tiy
# Creates a directory called tiy
$ cd tiy
# Working directory should change
$ ls
# There shouldn't be any files in here yet - we just made it!
```

You can also create files from the command line. The `touch` command creates a file if it doesn't exist, and also updates its _last modified_ time to the current time (hence the name `touch`).

```bash
$ touch newfile.txt
$ ls -la
# You should see newfile.txt
```

It's even possible to edit files directly from the command line (though you are best off using a real text editor for any serious editing). You can use the `echo` command, combined with the redirect operator `>`, to write to a file.

```bash
$ echo "Hello, Iron Yardigans" > newfile.txt
$ ls -la
# newfile.txt should now have a non-zero size
```

### Examining Files

So now we've created a file, and we can see that it isn't empty, but we haven't yet confirmed what's in it. Since we could look inside the file from Finder, we should assume that it's possible to look inside it from the terminal - and we'd be correct!

If we want to use the system application to open a particular file, we can use the `open` command:

```bash
$ open newfile.txt
# This will launch the default system application for .txt files
# (Probably TextEdit)
```

If we wanted to do any serious editing, we probably should use an editor like TextEdit or Atom. But what if we wanted to just look at the contents really quickly, without leaving the terminal?

The `cat` command will simply print out the contents of files we pass it:

```bash
$ cat newfile.txt
# You should see Hello, Iron Yardigans
```

Why `cat`? It's short for _concatentate_ - you can actually pass many filenames to `cat`, and it will print out each of them, _concatenating_ them together.

If you have a long file, though, `cat` can be frustrating, because it will print the WHOLE file. For that, it's often handy to use a program called `less`:

```bash
$ less newfile.txt
```

`less` shows you just one screenful of information at a time - you can use the arrow keys or the `vi` navigation keys (`j`, `k`) to move around the file. Pressing `space` will skip down a whole screen. When you're done looking at the file, press the `q` key to quit.

### Copying, Moving, and Renaming

In Finder, you can copy files by holding down `⌘` and dragging a file somewhere. Use the `cp` command to _copy_ files in terminal:

```bash
$ cp newfile.txt newcopy.txt
# Creates a file called newcopy.txt that is a copy of newfile.txt
$ cat newcopy.txt
# The contents should be the same
```

You can _move_ files using the `mv` command:

```bash
$ mv newcopy.txt ../
# Moves newcopy.txt to the parent directory
$ cd ..
$ cat newcopy.txt
# The contents should still be the same
```

Renaming is as easy as moving - because it actually **is** moving! Rather than specify a directory, though, you specify the _new filename_ you want to use, like this:

```bash
$ mv newcopy.txt specialfile.txt
$ cat specialfile.txt
```

### Erasing

Finally, you may want to remove a file using the command line.

#### Warning!

When you remove files using the method we're about to discuss, they **do not** go into the trash - they are removed from your system completely! Be very careful using `rm` - it is a potent tool. You may want to install the tool `trash` and use it instead of `rm`.

Okay, now, let's say you actually do want to get rid of some files. The `rm` command _removes_ files from your filesystem.

```bash
$ rm newfile.txt
$ ls
# newfile.txt should be gone
```

This deletes the file completely, without any warning. Be **very careful** with this command - it is a sharp knife!

If you want to remove a directory, `rm` by itself won't work. You can use `rmdir` to _remove_ an empty _directory_:

```bash
$ cd ..
$ rmdir tiy
$ ls
# tiy should be gone
```

If the directory is not empty, you can use `rm -r` to _recursively_ remove the directory and all of its contents. This is using a **giant** sharp knife!

Again - please consider using the `trash` utility instead. You can install it using `brew install trash`.

### The OS X Filesystem

Now that we know how to navigate the filesystem, let's take a quick tour of some important landmarks. Why are we doing this at the terminal?

Well, it turns out that Finder only shows you _part_ of the filesystem. Even if you have Finder set to show all hidden files and folders, there are several top level directories that it hides away. At the terminal, we can see **everything**.

### The Root

The highest-level directory is `/`, often referred to as the _root directory_. You can get there using `cd`:

```bash
$ cd /
$ ls
```

Some of the folders at the root level might be familiar to you: `Applications` is where all of your Mac apps are installed, and `Users` contains your home folder. Some others might be new to you, though. Many of these folders have their origins in the Unix roots of Mac OS X, and have equivalents on Linux/Unix servers.

#### `/bin`

`/bin` contains **critical** system _binaries_, or "runnable" programs. If you take a look inside this folder, you should see some familiar commands:

```bash
$ cd /bin
$ ls
# cat, cp, echo, ls, mkdir, mv, rm...
```

#### `/dev`

`/dev` contains **virtual** files that point at various _devices_ connected to your computer. This allows programs to interact with physical hardware using a standard interface.

#### `/etc`

`/etc` contains system-wide configuration files and information related to the system services. One of the files in here of particular note is `/etc/hosts`, which can be used to give custom names to servers on the internet.

#### `/sbin`

`/sbin` contains _system binaries_ that generally require superuser (`root`) privileges to run. More about privileges below!

#### `/tmp`

`/tmp` is a place to create _temporary_ files. These are not guaranteed to exist for any period of time, but many programs can safely write and read from this directory.

#### `/usr`

`/usr` is a place to store system-specific files, including binaries that are intended to be run by non-superusers and aren't critical.

#### `/var`

`/var` contains files whose contents are _variable_ - that is, they are expected to change frequently. Often, log files are kept here.

### Permissions

Something we've glossed over so far is the concept of file _permissions_. Every file and directory in the filesystem has a set of permissions attached to it. These permissions define what users can interact with a file/directory, and what they're allowed to do with it.

There are three types of users associated with a filesystem object (file or directory):

* The **owner**
* Members of the object's **group**
* Everyone else (the **others**)

There are also a few pertinent types of actions allowed with a file:

* **Reading** it
* **Writing** to it
* **Executing** it
	  * If the object is a directory, this means the ability to `cd` into it
	  * If the object is a file, this means the ability to **run** it like a program

When you perform `ls -la`, you can see the permissions associated with objects. For instance, here are some of the lines when I perform `ls -la` in my home directory:

```
drwx------+  156 james  staff    5304 Jan 31 09:48 Pictures
drwxr-xr-x+    5 james  staff     170 Jul 24  2015 Public
```

Both `Pictures` and `Public` have `james` as the **owner** and `staff` as the **group**. The _permissions_ are shown to the left.

First, we see `d`, indicating that they are _directories_. Next, we see the permissions allowed for the **owner**: in this case, `r` means **read**, `w` means **write**, and `x` means **execute**.

`Pictures` only allows me (the owner) to read, write, or execute. `Public`, on the other hand, has additional permissions - both the group (`staff`) and everyone else have `r` and `x` permissions, meaning they can `cd` into the directory, and also **read** the contents. However, they can't **write** to any files in the directory.

If I wanted to allow other members of the `staff` group to write to the `Public` folder, I can use the `chmod` command:

```bash
$ chmod g+w Public
$ ls -la
# drwxrwxr-x+    5 james  staff     170 Jul 24  2015 Public
# Group should have write permissions now
```

`chmod` takes a parameter that is made up of the **who**, a `+` or a `-`, and the **permission** to grant or take away.

* **who** can be `u` for the _user_ who owns the file, `g` for the _group_, `o` for _others_, or `a` for _all_ (everyone)
* `+` means to grant the permission, `-` means to take it away
* **permission** can be `r` for _read_, `w` for _write_, or `x` for _execute_

#### Ownership

When you create a file, you are automatically set as the file's **owner**. Ownership can be changed, though, by using the `chown` command. `chgrp` can change the file's group. Both of these commands should be used with care.

#### The Superuser

The **superuser** (also known as `root`) is a user that has full system permissions. Even if a user marks a file as being only usable by the file owner, `root` can access it. `root` is also capable of performing system-level operations.

Any time a window pops up asking you to type in your password to perform system level operations, you are essentially giving a program permission to run as the superuser.

Because `root` is so powerful, it's a standard security practice **not** to log in as `root`, but rather to just run specific programs at _elevated privileges_ as needed. You may need to do this at the terminal, generally when making system-wide changes.

To run a program at the terminal with elevated privileges, you use the `sudo` command, followed by the command that needs system level privileges. For example, you can use the following command to restart your computer from the terminal (**please be sure to save all work before trying out the command!**):

```bash
$ sudo reboot
# A password prompt will appear. Type in your user password, and press return.
# Note that there will be no visual indication that you are typing.
# When you press return, the system reboots without warning!
```

When installing packages systemwide, you will often need to use `sudo`. Just be aware that `sudo` is very powerful, and with great power comes great responsibility. Try to understand what the command will do before running it with `sudo`, and you will avoid many pitfalls.

### The Shell

Every interaction where you've typed a command in the terminal, you've been interacting with a **shell** - a program that accepts commands and runs them. Specifically, you've likely been using a program called `bash`, the _Bourne Again Shell_, unless you've changed your shell to another one. Other common shells include _C Shell_ and _Z Shell_.

On the surface `bash` might seem pretty simplistic, but it actually features a lot of power. It is possible to write full featured programs in `bash` - it supports variables, conditional expressions (`if`/`else`), functions, and loops!

### The Prompt

The **prompt** is what is displayed to you by the shell when it's ready to accept a new command. The default prompt on OS X looks like this:

```
<hostname>:<working directory> <username>$
```

For development, though, you may want to customize your prompt. For instance, you may want to include the branch and whether or not there are uncommitted changes right on your prompt. There are a number of ways to do this - one of the simplest is to switch to `zsh` using [Oh My ZSH!](http://ohmyz.sh/).

#### Oh My ZSH!

You can install **Oh My ZSH!** by running the following command:

```bash
$ sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

This will download **Oh My ZSH!** and set `zsh` as your shell. Your prompt will be different, too: it will now use some color coding and show your `git` status. There are many themes to choose from bundled with **Oh My ZSH!** that include different information. You can customize your shell by editing the `.zshrc` file in your home directory.

If you decide you want to uninstall **Oh My ZSH!**, run the following command:

```bash
$ uninstall_oh_my_zsh
```

### Variables

Whether you are using `zsh` or `bash`, your shell keeps track of **variables**. These work similarly to variables in other programming languages, except they are often accessible by programs you run inside the shell.

You can see a list of variables currently defined by running the `export` command:

```bash
$ export
# Variables and their contents
```

#### `PATH`

One very important variable is the `PATH` variable. You can see what's in a variable by running the following command:

```bash
$ echo $PATH
# Something like /usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin
```

Note that the `$` character is used to tell the shell that you are about to give it the name of a variable.

The `PATH` variable is used to search for programs. When you type a command at the shell prompt, the shell will look through each of the directories listed in `PATH` until it finds a directory with the program you specified.

If you install a program to a directory other than the ones listed in the `PATH`, you may need to modify your `PATH` to support running it without specifying the full name of the file every time.

### Using the Shell Well

Different shells offer different shortcuts/methods for working with them, but both `zsh` and `bash` allow for some shared core functionality.

#### Command History

If you need to re-run a command, or modify it slightly, you can use the `↑` and `↓` arrow keys to select between previous commands. `←` and `→` arrows let you move left and right in the current command. If you just want to run the command as-is, press `↑` until you find the command and then press `return`.

#### Filename Completion

Typing out filenames can be very tedious. Because of this, shells let you press the `tab` key to _complete_ the file or directory you have started typing. If there is only one possible match, then it will complete the whole name. If there are multiple possible matches, `zsh` and `bash` act a little differently: both will complete up to the point that they diverge, at which point `zsh` will show you a list of possibilities. `bash` requires pressing `tab` one more time to see the list of possibilities. Continue typing the name you are looking for, and you can again press `tab` when you've typed enough for the selection to be unique.

For example, if you wanted to go to the `Pictures` directory, you could type the following:

```bash
$ cd Pi
```

At this point, you can be reasonably certain that there are no other folders that start with `Pi`, so you can press `tab`, and `bash` automatically completes the command to the following:

```bash
$ cd Pictures/
```

You can then press `return` to execute the command, or if you want to go to a folder inside `Pictures`, continue typing parts of the folder and pressing tab as necessary.

A nice side benefit of tab-completion is that you can be aware of typos. If pressing `tab` doesn't give you any results, you likely mistyped something somewhere!

#### Globbing

Sometimes, you want to perform an operation on more than one file. This could be copying files, moving files, removing them, or even opening them up in an another program. Many commands let you specify multiple files on the command line, like this:

```bash
$ cp file1.txt file2.txt file3.txt Downloads
# Copies three files to the Downloads directory
```

That can be very tedious if you want to copy many files! Thankfully, it is possible to use a technique called **globbing**, if the files you want to copy fit a particular pattern. For instance, if you wanted to copy all the `.txt` files, you could do the following:

```bash
$ cp *.txt Downloads
# Copies all files ending in .txt to the Downloads directory
```

`*` means "match everything", so specifying `*.txt` means "match everything that ends with .txt". You can match all non-hidden files by simply specifying `*` by itself as a parameter. If you want to match hidden files too, you'll need to add `.*` to include files that start with `.`.

Globbing can save a lot of typing!

### Stopping

Sometimes, you might start a command that's taking too long, or realize you mistyped a command. You don't need to press the `x` in the corner of the terminal window to quit a particular running program - you can do that from within the shell too!

Pressing `^C` (`^` is the `control` key) will _terminate_ most active processes. Sometimes, for instance, when the process is a shell-type program, `^C` just terminates the current line. If you want to completely quit these, you can often press `^D`, which these programs will interpret as the end of usable input.

If you are using a program like `less`, though, neither `^C` nor `^D` quit! `less` uses keys inspired by the text editor `vi`, and as such, quitting it can seem a little tricky. Usually just pressing the letter `q` will quit these programs. Sometimes, you may need to press `esc` and `:` first, followed by `q` and `return`.

### Special Characters

One last trick when working with shells: as mentioned above, `$` has a special meaning in the shell. There are many other characters that have special meanings too - most punctuation characters especially have special meanings.

If you wish to use special characters in the command line, or if you are dealing with filenames that have spaces or special characters in them, you will need to handle them specially. The simplest way to do this is to use the `\` character immediately before a special character.

For instance, to create a file called `foo?.txt`, run the following command:

```bash
$ touch foo\?.txt
$ ls
# foo?.txt should exist
```

You can also put single quotes (`'`) around filenames if you want to use special characters. This works for most special characters except for single quotes themselves - those must be escaped using `\`:

```bash
$ rm 'foo?.txt'
$ ls
# foo?.txt should be gone
```

Double-quotes (`"`) can be used similarly, except that they actually preserve **some** special character meanings. When in doubt, use single quotes!

### Getting Things Done in the Terminal

There are quite a few useful utilities that can be accessed from the terminal.

#### Installing New Programs with `brew`

If you come across an unfamiliar tool, if it's considered a "standard" Unix program there's a good chance you already have it. You can see if it's already in your current path by using the `which` command:

```bash
$ which grep
# /usr/bin/grep
```

`which`, by the way, tells you _which_ program it finds by searching the path. If you try searching for a program that isn't already installed, it will not return anything:

```bash
$ which madeupprogram
# No result
```

If you want to use a program that you don't already have installed, there's a decent chance it is installable using [Homebrew](http://brew.sh/)'s `brew` command. Many of these can be installed by running `brew install`:

```bash
$ brew install cowsay
# Installs cowsay if it isn't already installed
$ cowsay 'I love working with the terminal!'
# A lovely picture of a cow appears
```

If that doesn't work, you'll need to determine what package(s) are necessary to install in order to use the program on your computer, or possibly build it from the source code if it's an open source project. It may still be possible to get the program from homebrew, and this will generally be the easiest route!

#### Searching Text with `grep`

`grep` is a utility that searches through files/output. It can be used to search plain text files. For instance, to look for all mentions of **tiy** in files in the working directory, you could run the following command:

```bash
$ grep 'tiy' *
```

`grep` is also really useful when used with **pipes**. A pipe is a way of taking output from one program, and passing it into another program.

As an example, let's say you can't remember a command you typed relating to cows. Was it `cowthink`, `cowmoo`, `cowcow`...?

There's a builtin command called `history` that shows you the things you've recently typed at the terminal:

```bash
$ history
# Many previous terminal commands
```

But that is way too many things to look through by hand! We can _pipe_ the output to `grep`, though, like this:

```bash
$ history | grep 'cow'
# Only lines that have the string "cow" in them will be shown
```

#### Editing Files with `vim` and `nano`

Although using a windowed application text editor offers many advantages, sometimes you may find yourself needing to edit text files in a terminal. There are a few tools that are usually available in most Unix-like environments: `nano`, `vim`, and `vi`, in increasing order of complexity.

##### `nano`

`nano` is perhaps the easiest to pick up without training - it doesn't require memorizing any keyboard shortcuts, and the default behavior acts very similar to many graphical text editors.

```bash
$ nano newfile.txt
```

Pass in the name of a file you want to edit. If the file doesn't exist, it is created automatically.

At the bottom of the screen, the keyboard shortcuts are displayed. Remember that `^` refers to the `control` key on your keyboard. A common workflow is to open a file using the `nano` command, save, and quit. You can do this quick-ish by pressing `^X` (to _exit_), then hitting the `Y` key to indicate you want to save changes. `nano` will then confirm the name of the file you want to save. You can press `return` to accept the name you already typed, and then it will quit.

If you want to quit _without_ saving changes, just press the `N` key instead of `Y`.

##### `vi` and `vim`

`vi` and `vim` (_Vi IMproved_) are much more powerful text editors, but they have a significant learning curve. They are available on nearly every Unix-like system, though, so it's good to be a little bit familiar with them, even if you don't use them for everyday coding.

You can use your arrow keys to move around files, but if you try to start typing, you might be surprised at what comes out. This is because until you enter **insert mode**, you are not able to make changes. To make changes to a file, press the `I` key on your keyboard first, and then you can begin typing like normal. If you press `esc`, you will be put back into **normal mode**, which is meant for navigating files.

When you are done editing a file, you need to type a command to save and/or quit.

Press the `esc` key to get back into **normal mode**, then type `:wq` if you want to _write_ the file (save it) and _quit_, or type `:q!` if you want to _quit_ without saving changes (the `!` indicates you're aware that you're quitting without saving).

By the way, it is perfectly fine to use `vim` for everyday coding - it is highly customizable and can do many of the things that windowed applications can do. Just be aware that you're going to have to invest some time learning it!
