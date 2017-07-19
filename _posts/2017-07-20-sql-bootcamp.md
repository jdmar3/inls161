---
layout: post
title: "Database software and MySQL"
era: Data
tags: 
- database
- SQL
- MySQL
date: 2017-07-19 11:30
end_date: 2017-07-19 13:00
category: class
---

Today we will jump head-first into working with databases as an extension of our discussions earlier in the week about data.  
<excerpt/>

A "database" is a collection of information, arranged or organized in some meaningful way so as to aid the retrieval of that information. 
The types of information stored in databases vary based on the purpose and application. 

When we refer to databases now, we usually mean electronic databases or DataBase Management Systems (DBMS). 
However, databases can exist in a number of non-electonic forms (and have for much of human history).

What are some examples of non-electronic databases?

# What goes into a database?

Pieces of information, or objects, are stored in a database in a structured way. 
The objects are sorted into classes according to type. 
This approach is referred to as "object-oriented," which we have briefly touched on over the course of the semester. 

When data are entered into a database, each object, or chunk of information, is assigned a class that allows for sorting and recall. 

## How does the information go in? 

There are a number of different ways to get data into a database. 

We can import tables directly from files. 
We can also input data one at a time using an entry form. 
We will do both of these things over the next few days. 

Today we will start by experimenting with opening the CSV we made the other day as a table. 

## Electronic DBMS

There are myriad choices for DMBS implementations. 
A commonly used system is called MySQL, which is based in a database language called SQL (Structured Query Language). 

You will also hear of NoSQL databases, such as MongoDB. 
These use an entirely different internal logic to store and recall data that that of SQL-based systems. 

There are a great many front-end user interfaces for these systems. 
MSAccess has been used for years for all sorts of applications. 

We will use the LibreOffice Base package. 
It is an open-source analog to Access and will allow us to do the same things. 
One major benefit of this is that we will be able to open our database without being locked to MSAccess. 
At present, there is no way to open an Access DB in another program. 
We wish to avoid that. 

# Install MySQL

We will install MySQL so that we can create and explore a database using the SQL shell in our CodeAnywhere containers.

# System maintenance

First update and upgrade all packages:

```sudo apt-get update && sudo apt-get upgrade```

We will need to make some space on our containers to install MySQL. 

We no longer need `unoconv`, so let's get rid of it:

```sudo apt-get remove unoconv```

When that is done, we can remove all of its dependencies:

```sudo apt-get autoremove --purge```

And then just for good measure, let's clean out our package cache:

```sudo apt-get autoclean && sudo apt-get clean```

# Install the MySQL client and server packages

Then we have to install one dependency, without which the install will fail:

```sudo apt-get install bsdutils```

Then install both the MySQL server and client packages in separate commands. 

```sudo apt-get install mysql-server```

This will ask you to create a password for the MySQL root user. 
Since we are only trying things out today and not installing this for the purpose of running a real SQL server, just put ```changethis``` as the root password. 

Then install the client:

```sudo apt-get install mysql-client```

# For next time

Tomorrow, we will return to databases and discuss the conceptual and theoretical underpinnings of what we worked on today. 
I would like you to read something about databases.{% sidenote 'db' '“What Is a Database?” BBC Guides. http://www.bbc.co.uk/guides/z8yk87h.' %}

We will look at other resources and tutorials in class as well. 