---
layout: post
title: "Introduction to scripting"
era: Text 
tags: 
- Pandoc
- PDF
- LaTeX
- Bash
- Scripts
category: class
quiz: https://goo.gl/forms/6jQTCWkh8x0SKDec2
---

Today we will learn how to convert our plaintext Markdown into a PDF. 
To do this we will have to install some more software, which may take a while. 

In the mean time, we will cover some of the basics of scripting in order to be able to automate our workflows a little bit better. 
BASH scripting is a good skill to have exposure to if you ever use any Linux/UNIX-based system and have repetitive tasks that you could script instead of completing manually. 
<excerpt/>

# Texlive

The TeX (or LaTeX) distribution that we are using in conjunction with Pandoc is called "TeXLive." 
This software is in our CodeAnywhere container's repositories. 

It is very large, so we are only going to install the base package to avoid running out of space on our CodeAnywhere containers. 
We have a total of 2GB of space. 
TeXLive should take up an extra ~650MB of space. 

To check to see how much space we have, we can run this command in a terminal:

```df -h```

It will look something like this:

```
cabox@box-codeanywhere:~/workspace$ df -h
Filesystem          Size  Used Avail Use% Mounted on
/vz/private/669416  2.0G  1.1G  953M  54% /
none                128M  4.0K  128M   1% /dev
none                4.0K     0  4.0K   0% /sys/fs/cgroup
none                 26M   52K   26M   1% /run
none                5.0M     0  5.0M   0% /run/lock
none                128M     0  128M   0% /run/shm
none                100M     0  100M   0% /run/user
cabox@box-codeanywhere:~/workspace$
```

Make a mental note of the number in the first line of output. 
I have 953MB available. 

## Installation

Now, to get TeXLive installed on our CodeAnywhere containers, we'll need to use apt-get{% sidenote 'apt-get' '“AptGet/Howto.” Ubuntu Documentation - Community Help Wiki. https://help.ubuntu.com/community/AptGet/Howto.' %} just like we did for Pandoc:

```sudo apt-get install texlive```

That will output a bunch of stuff and tell us how much the installation will take up on disk. 
See if the number is smaller than your available space and then type `Y` and hit enter if you have enough space. 
If not, we'll have to clear something out so you can install it. 

This may take a while. 

If that command does not work, it is likely because you need to update your software source repositories and upgrade your installed software packages. 
You can do that with two commands:

```sudo apt-get update```

This updates the sources. Follow it with;

```sudo apt-get dist-upgrade```

This actually downloads and installs updates to the already-installed software. 

In the mean time, we can look at scripting. 

# Scripting

Scripting is fun when you get used to how it works. 
It is also really useful for not having to repeat the same work over and over again. 

Creating scripts is often a trial and error process, though, and can feel frustrating (see below).

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">What scripting feels like <a href="https://t.co/jYR9WQftIX">https://t.co/jYR9WQftIX</a></p>&mdash; SecuriTay (@SwiftOnSecurity) <a href="https://twitter.com/SwiftOnSecurity/status/749783791279939585">July 4, 2016</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

## How to do it?

In class today, we'll go over some basic scripting. 
We'll use William Shotts' tutorial.Writing Shell Scripts tutorial by William Shotts for tomorrow.{% sidenote 'shell-scripts' 'Shotts, William, Jr. “Writing Shell Scripts.” LinuxCommand.org. Accessed July 6, 2016. http://linuxcommand.org/lc3_writing_shell_scripts.php.' %} 

A basic Bash script is simply a list of commands in a file. 

The lines in the file get executed sequentially and then at the end of the file Bash stops, or waits depending on what the file tells it to do. 

### Execution

All shell scripts should be executable and specify what shell program will run them. 
If this is not the case, then we have to call a shell in the command line in order to run. 

To create a basic Bash shell script, just touch a new file and give it the extension `.sh`:

```touch hello-world.sh```

Then we'll make it executable:

```chmod +x hello-world.sh```

This command sets the execute flag for user, group, and anyone in the permissions. 
They should look like this if you list the files with long output:

```
cabox@box-codeanywhere:~/workspace/helper-scripts$ ls -lah
total 64K                                   
drwxr-xr-x 3 cabox cabox 4.0K Jul  7 12:44 .
drwxrwxr-x 5 cabox cabox 4.0K Jul  7 10:02 ..
-rwxr-xr-x 1 cabox cabox  104 Jul  7 12:50 hello-world.sh 
cabox@box-codeanywhere:~/workspace/helper-scripts$ 
```

We also need to add a "shebang" to our script to tell Bash to execute this file. Inside the `hello-world.sh` file, put this on the first line:

```
#!/bin/bash
```

### Echo

Now, we're going to make this script say hello to the world and hello to us. 
We do this by using the `echo` command, which outputs whatever you tell it as text to `STDOUT`. 
Try it:

```echo "Hello, world!"```

You should see this in the command line:

```
cabox@box-codeanywhere:~/workspace/helper-scripts$ echo "Hello, world!"
Hello, world!
cabox@box-codeanywhere:~/workspace/helper-scripts$
```

Now we will add this command to our script: 

```
#!/bin/bash

# Say "Hello, world!
echo "Hello, world!"
```

Now when we run this script, we will see the same output as from our earlier `echo` command on `STDOUT`:

```
cabox@box-codeanywhere:~/workspace/helper-scripts$ ./hello-world.sh
Hello, world!
cabox@box-codeanywhere:~/workspace/helper-scripts$
```

Note the `./` in front of the script's filename in the above command. 

We have to do this in order to execute files and scripts that are not in our execute path. 
The excecute path is just a list of directories from which we are allowed to execute files without jumping through some extra hoops. 
To see your path, use the following command: 

```
cabox@box-codeanywhere:~/workspace/helper-scripts$ echo $PATH 
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
cabox@box-codeanywhere:~/workspace/helper-scripts$
```

These are all the directories from which you can execute a program. 

Finally, we want to add a "Hello!" to ourselves, and use our GitHub username. 
We will add the same command as before, substituting our GitHub username for world, so that the script looks like this (I've used my own name here):

```
#!/bin/bash

# Say "Hello, world!
echo "Hello, world!"
# Say "Hello, YOU!
echo "Hello, jdmar3!"
```

Now if we run this, we will see all of this output:

```
cabox@box-codeanywhere:~/workspace/helper-scripts$ ./hello-world.sh
Hello, world!
Hello, jdmar3!
cabox@box-codeanywhere:~/workspace/helper-scripts$
```

## Tomorrow

We will pick up where we left off tomorrow during lab and get to work creating our scripts for the next assignment. 
Please review the tutorial on writing shell scripts again.{% sidenote 'shell-scripts' 'Shotts, William, Jr. “Writing Shell Scripts.” LinuxCommand.org. http://linuxcommand.org/lc3_writing_shell_scripts.php.' %} 
Also, we'll use another tutorial so that we can learn to create prompts for user input.{% sidenote 'user-input' 'Chadwick, Ryan. “User Input - Bash Scripting Tutorial.” Ryan’s Tutorials. http://ryanstutorials.net/bash-scripting-tutorial/bash-input.php.' %}
