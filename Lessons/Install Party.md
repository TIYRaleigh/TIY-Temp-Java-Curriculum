![install all the things.jpg](https://tiy-learn-content.s3.amazonaws.com/8a4890d6-install%20all%20the%20things.jpg)

### Java Development Kit 8

The Java Development Kit (JDK) is what turns the code you write into something the Java Runtime Environment (JRE) can actually execute on your computer. IE: It makes the magic work.

[Download the OS X version here.](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

![JDK download.gif](https://tiy-learn-content.s3.amazonaws.com/fe24512d-JDK%20download.gif)


### Install the Xcode command line tools

We'll need to use a few command line tools in this class. One of these is Git. Apple makes us jump through a small hoop the first time we try to use it. Let's get that out of the way now. Start by opening Terminal. This can be found in the Utilities folder under your Applications folder.

Once Terminal is open, type "git" shown below.

![Screen Shot 2016-03-04 at 4.18.09 PM.png](https://tiy-learn-content.s3.amazonaws.com/18ce3657-Screen%20Shot%202016-03-04%20at%204.18.09%20PM.png)

When you hit enter you should see the following dialog popup. If not, you're already in business.

![TN2339_InstallTools.png](https://tiy-learn-content.s3.amazonaws.com/a3df7d81-TN2339_InstallTools.png)

Just click the Install button and the command line tools - including git - will be installed for you.

### Git Config

We need to configure Git so it knows our email address and name.

```bash
git config --global user.name "<your name here>"
git config --global user.email <your email here>
```

### Generate an SSH key and setup a Github account

SSH stands for Secure Shell and is used to communicate securely across the internet. It's similar in nature to how your browser talks to a secure website.

We will be using a tool called Git to track changes we make to our programs in this class. We will also be using an online service called Github. Behind the scenes, Git uses SSH to communicate over the internet with Github. For this to work, we need to create an _SSH key_. An SSH key is like an ID your computer can use to prove to other computers that you are who you say you are.

To create your SSH you will need to open Terminal again and type `ssh-keygen`, as shown below. Hit enter and accept the defaults.

![Screen Shot 2016-03-10 at 12.49.02 PM.png](https://tiy-learn-content.s3.amazonaws.com/145b68f9-Screen%20Shot%202016-03-10%20at%2012.49.02%20PM.png)

Now, go to http://github.com and create an account and log into it. Open your account settings, click on SSH keys, and create a new SSH key. Give your key a name and paste your key into the 'key' text field.

![github setup.gif](https://tiy-learn-content.s3.amazonaws.com/7e31a516-github%20setup.gif)

### Homebrew

Homebrew is a package management tool for OS X that makes it easy to install a wide range of open source tools.

To install Homebrew simple run this script in terminal:

```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

Follow the instructions in the terminal to complete the process.

### IntelliJ 15 Ultimate

IntelliJ is an Integrated Development Environment (IDE). It provides a ton of powerful tools that make it easier to write and test Java code.

We will be using IntelliJ 15 Ultimate in class. I will provide you with a student license you can use for the duration of this class. After this class, The Iron Yard can help you purchase your own license at a discount. If you do not yet have a license for IntelliJ, it can be run as a trial for up to 30 days.

* [Download IntelliJ Ultimate here.](https://www.jetbrains.com/idea/download/)

#### Basic IntelliJ Configuration

Let's take care of some housekeeping before we get started with class. When you first start IntelliJ it will ask you a bunch of questions. If you have already received your student license information, go ahead and provide that. Otherwise, just go ahead and accept the default options.  You might also want to keep IntelliJ in the dock.

![IntelliJ initial startup.gif](https://tiy-learn-content.s3.amazonaws.com/034927f0-IntelliJ%20initial%20startup.gif)

### That's it!

Now that you're done with that, you're ready to roll on the first day of class!
