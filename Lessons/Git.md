## Source Code Control

Software projects are made from _source code_. Source code is the collection of files that are created when making a software project. In this class much of that will be `.java` files that contain code written in the Java programming language. It will probably also include other textual files with extensions like `.xml`, `.json`, and `.pom`. Additionally you'll probably have image files and other types of resources. All of these together make up your software project. 

Programming is labor intensive. If it were easy, everyone would do it. Sometimes it can take days or weeks just to make a small feature of your program work the way you want it to. It can also be a fine craft, like painting, sculpting, or woodworking. As they say, rome wasn't built in a  day. This labor and time has value, so you need to protect it.

![safe deposit box.jpg](https://tiy-learn-content.s3.amazonaws.com/47741bfe-safe%20deposit%20box.jpg)

<!-- todo: make an analogy about how SCC (not distributed) is like safety deposit boxes. You make an important document (will, business contract, whatever) and take it and deposit it. -->

I think everyone who has ever used computers has had an experience where they lost work. Who hasn't stayed up past midnight writing a report for school, only have the power go out and realize and realize they hadn't saved the last two hours of work? Who hasn't spent hours revising a document only to realize it was better before they started mucking around in it? 

This is where _source code control_ comes in. Source code control is a way to protect your hard work writing software. With source code control, you can save versions of your files as you make changes. You can safely make changes, even delete files, secure in the knowledge that you can always roll back time. 

But, be warned, _you_ need to tell the source code control system to save these files. You can't just hit cmd-s in your editor, you need to run a specific command on the command line or in another program to save a new version of your files. In this class you will learn to _commit_ your changes several times a day. A commit is how you save a version of a file. 

## Distributed source code control

It's awesome to be able to protect your files as you make changes. But, what happens if your hard drive fails? What if your computer is stollen? Your work is still lost! 

Because of this, source code control systems usually have a central server that actually holds a copy of your code and all of the changes. Historically this has been one all-important server that holds the gold-standard code. All developers on a project must always have access to this repository. 

This is good because servers can be made redundant so the loss of a hard drive or even an entire computer doesn't cause the loss of your source code. It also allows multiple programmers to share and collaborate on the same set of source code files. 

This is bad if a programmer is somewhere where they can't access this central repository. In this scenario a developer on an airplane (without wifi) cannot save their changes to the repository, get changes their coworkers made, or restore previous versions of files.

This is where _distributed source code control systems_ come in. A distributed source code control system is one where there is no king-of-the-hill central repository. There _can_ be, but there doesn't have to be. 

![home-safe.jpg](https://tiy-learn-content.s3.amazonaws.com/28ddca6b-home-safe.jpg)

<!-- todo: DSCC is like having a safe in your home. You can store valuable documents there. You can ALSO take copies to your safety deposit box. -->

With distributed source code control you have a full copy of the repository on your computer. You coworkers have full copies on their computers. A central server can also have a copy that is used to share code with the entire team. Yet another server can exist somewhere else for whatever reason. Perhaps a team in India wants their own central repository where they share their changes internally. When ready they share their changes company-wide.

As you make changes, you can save these changes to your own copy of the repository. When you're ready (and able) you can copy your changes to other repositories that other developers may have access to. 

Git is a distributed source code control system.

## Working Directory

You can create a new Git _repository_ in any directory on your computer. The repository is the metaphorical home safe where you can keep important documents. This process of creating a new repository is called initializing the repository. The directory where you initialize your new repository is called your _working directory_. All of the files and subdirectories your working directory _can_ be protected with Git after you initialize  repository.

However, take note that I used the word can. Git doesn't automatically know what files you want to manage. 

## Three step process

There are three distinct phases when working with Git.

### 1. Modify
	
The first stage is what happens when you create, edit, or delete files. Git isn't actually involved in this point at this point. You don't have to do anything special, just write code.

### 2. Stage

Before Git can protect a file you need to _stage_ it. When you stage a file you notify Git that you intend to _commit_ a specific version of the file. A commit is what it's called when you save a specific version of a file or a set of files into your repository. 

The staging area, also called an _index_, is where Git stores the specific version of your file or files when you stage them. 

It's important to note that just staging a file isn't the same as committing them. You can still edit a file and re-stage it without recording the change in your repository history. 

In a nutshell, the staging area is just a list of files you want to commit. 

### 3. Commit

Once you have added files to the staging area you can commit them. When you commit, you are instructing Git to record the files in the staging area into a record in the repository history. Now these files are protected!

## Using Git

We're going to be using Git on the command line. While there are many graphical user interfaces for Git, behind the scenes, they all just use the Git command line programs. Also, not all of the visual tools expose the full range of features of the Git command line. This has a couple implications:

1. If Git is being used, the Git command line tools are always available.
2. The Git command line tools are consistent.

By learning Git on the command line you can more easily understand most graphical Git clients. However, understanding a graphical Git client doesn't help you understand the command line.

## Common Git commands

All commands in Git begin with `git`. I'll review some of the most command commands here, but not in detail. Be sure to read the section on `git help` to learn how to learn more.

### git

**Syntax:** `git <command> <optional arguments>`

The entry point into Git is the command line program `git`. All of Git's capabilities are accessed through the `git` command by s. By default, if you just type `git` you will see a list of common Git commands:

![git command.png](https://tiy-learn-content.s3.amazonaws.com/007c32ed-git%20command.png)

This screenshot shows basic command line arguments and common Git commands. For example, you can see that `git --version` will show you the version of Git you have installed:

![git version.png](https://tiy-learn-content.s3.amazonaws.com/60f57ca8-git%20version.png)

But, in general you will specify a specific Git command to execute. The output from running `git` shows several commands like `init`, `add`, `commit`, `log`, etc. I'll go over the most common ones here.

### git help

**Syntax:** `git help <command>`

The git help command is your entry way into a vast store of knowledge about how Git commands work. If you just execute `git help` you will see the same output as if you ran just `git`.

But, you can take one of the many commands listed here and get more information by typing `git help` followed by the command name. For example, to learn more about the `init` command you can run `git help init`. This will open the _man page_ for the `git init` command. A man page is standard form of documentation on Mac OS X and other computers. 

![git help init.png](https://tiy-learn-content.s3.amazonaws.com/ee841ab0-git%20help%20init.png)

You can scroll up and down in a man page using your arrow keys. The space key will scroll down one page at a time. To exit out of the man page viewer you press `q`.

### git init

**Syntax:** `git init`

The `init` command is how you create a new repository in your working directory. It's very simple: just go to a directory you want to protect and type `git init`. This will create a hidden `.git` folder and your current directory will become your working directory.

![git init.gif](https://tiy-learn-content.s3.amazonaws.com/e650f69f-git%20init.gif)

### git status

**Syntax:** `git status`

The status command is used to show the current status of your working directory. It will show you new files that are not yet tracked in the repository, files that are tracked and have been modified, files that are tracked but have been deleted, what is in your staging area, and other useful information. 

This command is extremely useful to determine what to add to the staging area. It's also useful to see what's changed since your last commit. 

![git status.gif](https://tiy-learn-content.s3.amazonaws.com/00188f58-git%20status.gif)

This example shows how a new untracked file appears in the output from `git status`.

### git add

**Syntax:** `git add <file name>`

The `add` command is used to add files to your staging area (also called the index). You need to add files to your staging area before you can commit changes to them. There's a corresponding `rm` command that can be used to remove a file from the index.

You can see what files are staged using the `git status` command.

![git add.gif](https://tiy-learn-content.s3.amazonaws.com/158fd152-git%20add.gif)

This example shows how the output of `git status` changes once you've added a file to the staging area using `git add`.

### git commit 

**Syntax:** `git commit -m "<commit message>"`

The `commit` command is what takes the content in your staging area and records them into the repository. A commit will record the date and time, file changes, who made the change, a commit message explaining what was done, and a _SHA-1 checksum_. A SHA-1 checksum is a unique identification for this specific version of your repository. A SHA-1 checksum (SHA, for short) looks like this: `d670460b4b4aece5915caf5c68d12f560a9fe3e4`. 

A commit also empties out the staging area, cleaning it up for your next commit.

A commit message is required and should be descriptive of the changes made in this revision. For example, if you fixed a nasty bug in the thingamabob, then you should add a short message explaining what you did to fix the thingamabob. 

![git commit.gif](https://tiy-learn-content.s3.amazonaws.com/a56720f7-git%20commit.gif)

In this example I commit the `hello.txt` file I created in earlier examples.

### Important note regarding workflow

So far we've seen how to create a new repository, how to add files to the staging area, and commit them. This process is repeated over and over and over as you work. You should commit frequently throughout the day as you work. 

![git add edit delete.gif](https://tiy-learn-content.s3.amazonaws.com/0fa55b67-git%20add%20edit%20delete.gif)

In this example I repeat the process we saw above to edit our file, add another file, and then delete the new file. 

### Git log

**Syntax:** `git log`

The `log` command outputs the history of changes to your repository. 

![git log.gif](https://tiy-learn-content.s3.amazonaws.com/a45a7e88-git%20log.gif)

As shown in this example, I can see the history of commits to the example repository. Each of my commits is listed, with the most recent first. Each history entry shows the SHA, the committer, date, and commit message. 

There are many ways to format and filter the output from `git log`. One such example is `git log --name-status` which also includes files in the commit and their status. If you want more information, be sure to read the doc page for this using `git help`.

![git log name status.png](https://tiy-learn-content.s3.amazonaws.com/a2b017c5-git%20log%20name%20status.png)

This screenshot shows the output from `git log --name-status`. The most recent commit lists the `date.txt` with a `D` next to it. This indicates that the file was deleted. `A` means the file was added and `M` means the file was modified.

## Common Git commands when working with remote repositories

In class, as in most professional environments, we will be using remote Git repositories. These are distinct, separate, remote copies of our repository that we will push changes into and potentially pull changes down from. 

The first thing you need to do when working with a remote repository is either clone it, making a local copy of the repository, or set it as a remote repository for an existing local repository.

### Git remote

**Syntax:** `git remote`

The remote command is used to manage configured remote repositories. For example, if you initialize a local repository and later want to share it on Github, you will need to add a remote.

This screenshot shows a new repository I created in Github. I've highlighted the Github repository's SSH url. This is what we will use when adding the new remote repository to our local repository. 

![New Github repo.png](https://tiy-learn-content.s3.amazonaws.com/e226bf9b-New%20Github%20repo.png)

The syntax for adding a remote repository is `git remote add <SSH url>`. You can use `git help` to find more information on how to manage configured remote repositories in your local repository.

![git remote add.gif](https://tiy-learn-content.s3.amazonaws.com/264bc7f0-git%20remote%20add.gif)

This screencast shows how I'm adding a new remote repository to my local repository. I named the remote "origin" as this is the typical name for a single central shared repository. You could give this any name you want. You can also add as many remote repositories as you would like. For the purposes of our class we'll only need one remote per project.

### Git clone

**Syntax:** `git clone <SSH url>`

You can clone a remote repository using its SSH url. For example, if you wanted to clone a Git repository from Github you first find it's SSH URL. This screenshot has the SSH url for a Github repository highlighted.

![github ssh url.png](https://tiy-learn-content.s3.amazonaws.com/3d141141-github%20ssh%20url.png)

To clone the repository you simply execute the clone command. The repository will be cloned into a directory named after the repository.

![git clone.gif](https://tiy-learn-content.s3.amazonaws.com/63d3e21e-git%20clone.gif)

### Git pull

**Syntax:** `git pull <remote name> <branch name>`

The `pull` command is used to pull down commits that exist in a remote repository that do not exist in the local repository. This is most useful when working on a team. Perhaps another team member has pushed some changes to the remote repository that you need. You can pull these changes into your local repository using the pull command.

Most typically your remote repository will be named `origin`. Since we haven't discussed branching, it's safe to assume that the branch name will be `master`.

![git pull.gif](https://tiy-learn-content.s3.amazonaws.com/1740f9dc-git%20pull.gif)

This shows how changes that are in the remote repository can be pulled into the local repository

### Git push

**Syntax:** `git push <remote name> <branch name>`

When you're ready to share your code with a remote repository you can use the `push` command. The push command takes any commits in your repository that are not in the remote repository and copies them to the remote repository. 

Before this will work you must have all of the latest commits pulled down from the remote repository into your local repository. This is done using the `pull` command.

![git push.gif](https://tiy-learn-content.s3.amazonaws.com/65df508f-git%20push.gif)

This shows how code can be pushed into the remote repository. As with pull, we're assuming the remote is named `origin` and the branch is named `master`.
