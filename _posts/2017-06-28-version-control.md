---
layout: post
title: Version Control
era: Basics
tags: 
- version control
- git
- shell commands
category: class
quiz: https://goo.gl/forms/jFdTUhXcADOmi3IV2
---

Version control systems allow us to track and see the changes to a given document or set of files over time. 
This can be useful in situations where you wish to roll back changes or identify the point of origin for something problematic. 

It is also helpful when you are collaborating and want to be able to keep track of the work being done and changes being made by a group of people. 

Version control can exist in a standalone system or it can be networked and distributed. 
<excerpt/>

## Track changes

One expression of version control that we are probably all familiar with is the "Track Changes" function in MSOffice. 
It works if one person is using it to track changes between writing session. 
It also might work if two people are exchanging a document and each making changes when they have the document in their possession. 
Each handoff operates like a physical handoff in this case. 

But when you try to track changes with two people and then merge those documents, things become tricky. 
Which changes take precedence? 
How do you merge them together when you have both rewritten the same sentence? 

The process of merging becomes very difficult, very quickly and since the design of that interface wants to hide what is going on underneath, you might miss something and end up with a document that you did not mean to leave or leave something out accidentally. 

## Software source code

In the software development world, there are a number of systems that allow development teams to make small, incremental changes to the source code for a piece of software without losing work, breaking each others code, or stepping on each others fingers. 

The basic idea is that when you wish to make changes to a set of source code files, you have to check them out. 
This is just like checking out a library book, except that there are an infinite number of copies available and you can write on the pages. 
The object that you check out is called a repository. 
When you check it out, you get the source code files themselves, but you also get a whole bunch of metadata about them. 
The metadata includes information about when and how changes and merges have been made to the files as well as any user-generated information. 

Once checked out, you can make changes to the source files and then compile or test to make sure that your changes work. 
Then, once tested, you check them back in. 
Sometimes, the check-in process is fully automated, meaning that no human has to look to make sure that your changes make sense. 
Other time, the check-in needs to be verified. 
There are compelling reasons to use either of these scenarios. 

In such systems, each commit, or incremental change, is registered with a unique identifier. 
This means that the change is tracked and cannot be confused with any other change at any other time. 

When multiple parties are working on the same code, merging can be confusing, unless the changes are properly tracked. 
Version control systems allow us to make sure that merges go as smoothly as possible. 

## Distributed version control

In a fully distributed version control system (DVCS), multiple copies of the same repository can exist on different systems with different operators and still be elegantly reconciled as the same object. 
This means that work can be conducted asynchronously and then merged together later. 
Then length of time and amount of work done on each copy will have an effect on how easy or difficult it will be to merge the source back together. 
It is likely that if a long time occurs between merges, there will be some issues that crop up, particularly if a lot of changes are made. 

It is a good idea to keep your repositories up-to-date. 
It also acts as an easy back up system, if you are storing the repository off-site somewhere. 

### Distributed version control for document processing

Version control of this kind is not just for software development. 
It is possible to use it to manage your own workflow in creating and editing documents. 
It also works for managing different versions of datasets, from raw data to clean, ready-to-analyze data. 

In this course, we are going to use such a system to manage and back up our work.  

You should have read an article in preparation for this session about Git.{% sidenote 'githacker' 'Wynn, Joseph. “A Hacker’s Guide to Git.” Wildly Innacurate. Last modified May 25, 2014. <http://wildlyinaccurate.com/a-hackers-guide-to-git/>.' %} 
We will disscuss the fundamental concepts about version control contained in that article. 

Then, for the rest of today's class we are going to experiment with the version control systems that we will operate on and learn how to get our information into them and manage it once it is there.

# git

We will use Git as our version control system in this class. 
Git has an interesting past and was developed out of necessity. 

>**A Short History of Git**
>
>As with many great things in life, Git began with a bit of creative destruction and fiery controversy.
>
>The Linux kernel is an open source software project of fairly large scope. For most of the lifetime of the Linux kernel maintenance (1991–2002), changes to the software were passed around as patches and archived files. In 2002, the Linux kernel project began using a proprietary DVCS called BitKeeper.
>
>In 2005, the relationship between the community that developed the Linux kernel and the commercial company that developed BitKeeper broke down, and the tool’s free-of-charge status was revoked. This prompted the Linux development community (and in particular Linus Torvalds, the creator of Linux) to develop their own tool based on some of the lessons they learned while using BitKeeper. Some of the goals of the new system were as follows:
>
>Speed
>
>Simple design
>
>Strong support for non-linear development (thousands of parallel branches)
>
>Fully distributed
>
>Able to handle large projects like the Linux kernel efficiently (speed and data size)
>
>Since its birth in 2005, Git has evolved and matured to be easy to use and yet retain these initial qualities. It’s incredibly fast, it’s very efficient with large projects, and it has an incredible branching system for non-linear development.{% sidenote 'git-history' 'Chacon, Scott, and Ben Straub. “A Short History of Git.” In ProGit. New York, New York: Apress, 2014. https://git-scm.com/book/en/v2/Getting-Started-A-Short-History-of-Git.' %}

So, the development of Git is tied to the development of the Linux kernel, but it doesn't end there. 
It has come to be used in millions of projects and development workflows. 
Its versatility has also inspired people to develop new layers of interaction to work with it. 
We will discuss and explore one of those today and then use it for the rest of the semester. 

First, though, lets explore Git, starting with the elegantly designed [Git: The Simple Guide](http://rogerdudler.github.io/git-guide/) by Roger Dudler.

A more advanced and quite elegant Git tutorial is available here: [Git Tutorials and Training - Atlassian](https://www.atlassian.com/git/tutorials/setting-up-a-repository/git-config).

# GitHub

GitHub is a platform that allows for users to keep copies of their open source, plaintext repositories online, in a single centralized location. 
It also adds a social interaction layer to the process of managing version-controlled source files. 

It is useful for (and used by) software development projects as well as other plaintext-based projects, such as collaborative authoring of books and articles. 

It is particularly good for keeping track of projects that involve both plaintext source code or markup and files related to work that will be published using that code. 

Today we are going to learn to set up a repository locally

Tomorrow we will learn to push it to GitHub. 
We will also learn to set up a repository remotely on GitHub and then copy it locally. 

Please read up on the basics of GitHub in preparation for tomorrow's session.{% sidenote 'github-beginners' 'Orsini, Lauren. “GitHub For Beginners: Don’t Get Scared, Get Started.” ReadWrite. Last modified September 30, 2013. http://readwrite.com/2013/09/30/understanding-github-a-journey-for-beginners-part-1/.' %} 
The article in the notes has much the same information as some of the other articles and books referenced in our course site, but it strings the different parts together and makes for a useful review resource.