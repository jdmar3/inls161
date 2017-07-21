---
layout: post
title: "Database software and MySQL"
era: Data
tags: 
- database
- SQL
- MySQL
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

# Parts of a database 

## Tables

The basic storage template in a database is a table. 

This is simply a set of data arranged into columns and rows. 
Just like with the data that we generated previously, the rows represent lists of information that are related to a specific thing. 

The rows in our tables are called "records."

The columns then represent the types of information that we are organizing. 

Tables on their own are fine for storing a collection of data, but what if we have a lot of repeating data that we do not want to have to store over and over again in the same table?

## Relationships

The primary method of reducing this sort of data is by creating more tables and then defining relationships between them. 
This is why we refer to this type of database as "relational."{% sidenote 'Harkins, Susan. “Relational Databases: Defining Relationships between Database Tables.” TechRepublic. Last modified April 30, 2003. http://www.techrepublic.com/article/relational-databases-defining-relationships-between-database-tables/.<br/><br/>Harkins, Susan. “Relational Databases: The Inspiration behind the Theory.” TechRepublic. Last modified April 2, 2003. http://www.techrepublic.com/article/relational-databases-the-inspiration-behind-the-theory/.<br/><br/>The whole TechRepublic series on relational databases is useful. It would be worthwhile to read all of it. ' %}

There are three categories of relationship:

- One-to-One: Each record in a table has only one relationship to one other record in another table
- One-to-Many: Each record (by primary key) in a table can have zero, one, or many relationships to records in other tables. 
- Many-to-Many: Each record in a table can have any number of (or zero) relationships to records in other tables. 
 	
Can you think of any examples of relationships like this? 

### Primary Keys

A primary key, as mentioned above, is a designator associated with each record that distinguishes it from all other records. 
When creating a table with a one-to-many relationship, you will need to create a primary key for each new record. 

What are some possible pieces of existing information that might be used as a primary key?

What might be some problems with using an existing piece of information as a primary key?

## Queries

Queries take a set of instructions and use them to sort and categorize data across multiple variables and tables. 

We will look at different possibilities for queries and try some together in class. 

When we define relationships in the query designer, you'll notice that there are different joins available to you. 

## Joins

These are logical inclusion/exclusion criteria for your query at the table level. 
It is a good idea to have some understanding of what they do on a logical level.{% sidenote 'joins' 'Moffatt, C. L. “Visual Representation of SQL Joins.” CodeProject. http://www.codeproject.com/Articles/33052/Visual-Representation-of-SQL-Joins.<br/><br/>This visual  guide can help you to better understand each join and what they do.' %} 

Today, we will only use right joins in our example queries. 

Why would we do that?

# Electronic DBMS

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

# SQL Boot Camp

## Install MySQL

We will install MySQL so that we can create and explore a database using the SQL shell in our CodeAnywhere containers.

Destroy your container and create a new blank one.

## System maintenance

First update the software package repositories:

```sudo apt-get update```

And then just for good measure, let's clean out our package cache:

```sudo apt-get autoclean && sudo apt-get clean```

## Install the MySQL client and server packages

Then we have to install one dependency, without which the install will fail:

```sudo apt-get install bsdutils```

Then install both the MySQL server and client packages in separate commands. 

```sudo apt-get install mysql-server```

This will ask you to create a password for the MySQL root user. 
Since we are only trying things out today and not installing this for the purpose of running a real SQL server, just put ```changethis``` as the root password. 

Then install the client:

```sudo apt-get install mysql-client```

## Get some data

Let's download some CSV files that I prepared with a list of books in them. 

```wget http://inls161.johndmart.in/raw-material/tblBook.csv``` 

```wget http://inls161.johndmart.in/raw-material/tblPub.csv```

In order to avoid errors (due to restricted default priviliges settings in our MySQL installation) we need to move these files to a special location so that they can be loaded later. 

```cp tblBook.csv tblPub.csv /var/lib/mysql-files/```

This will allow us to load the data in the files in a later step.

# The MySQL prompt

Once we are all installed, issue the ```mysql``` command to get into the ```mysql>``` prompt:

```mysql -u root -p```

This specifies that you want to use the root user to login to the MySQL prompt. 

Next let's create a new DB. Make sure that your prompt looks like this:

```mysql> ```

If it does, then you can category:

```CREATE DATABASE booksinfo;```

Commands in the mysql> prompt are *case-sensitive,* so pay attention to the case of the commands. 

Let's list our DBs:

```show databases;```

We should see the DB with the name that we created in the list. Let's move into it:

```USE booksinfo;```

## Add tables

Now we have to create two tables so that we can import data from our CSV files.

```CREATE TABLE tblBook (ID INT, Title VARCHAR(255), Date INT, RetailPrice DECIMAL(5,2), Copies INT, ShelfNumber VARCHAR(255), PubID INT);```

```CREATE TABLE tblPub (ID INT, Publisher VARCHAR(255), City VARCHAR(255), State VARCHAR(255), Country VARCHAR(255));```

See what tables we have just created:

```show tables;```

Let's import some tables from the files we downloaded earlier:

```LOAD DATA INFILE '/var/lib/mysql-files/tblBook.csv' INTO TABLE tblBook FIELDS TERMINATED BY ',' OPTIONALLY ENCLOSED BY '"';```

This should give us some output. 
If we notice a warning, type the following to view the warnings:

```SHOW WARNINGS;```

So, it looks like we have a missing date. 
No big deal. 
We'll deal with that later. 
Let's import our other table. 

```LOAD DATA INFILE '/var/lib/mysql-files/tblPub.csv' INTO TABLE tblPub FIELDS TERMINATED BY ',' OPTIONALLY ENCLOSED BY '"';```

Let's see what is in our tables:

```SHOW COLUMNS FROM tblBook;```

```SHOW COLUMNS FROM tblPub;```

We'll notice that we have no key set for either table. 
We need to do this, right?

```ALTER TABLE tblBook ADD PRIMARY KEY (ID);```

Now look at the table again and see that it has changed:

```SHOW COLUMNS FROM tblBook;```

Now do the same for the other table:

```SHOW COLUMNS FROM tblPub;```

```ALTER TABLE tblPub ADD PRIMARY KEY (ID);```

# For next time

Tomorrow, we will return to databases and discuss the conceptual and theoretical underpinnings of what we worked on today. 
I would like you to read something about databases.{% sidenote 'db' '“What Is a Database?” BBC Guides. http://www.bbc.co.uk/guides/z8yk87h.' %}

We will look at other resources and tutorials in class as well. 