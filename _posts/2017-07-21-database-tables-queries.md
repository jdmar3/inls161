---
layout: post
title: "Databases, tables, queries, and relationships"
era: Data
tags: 
- database
- tables
- queries
- SQL
- MySQL
category: class
---

Today we will continue with our discussion of databases and then learn ALL THE SQL. 

![LEARN ALL THE SQL]({{ site.url}}/assets/img/learnallthesql.jpg)
<excerpt/>


## Define relationships

We need to tell MySQL that the PubID column in tblBook refers to the primary key in tblPub. This action is called a constraint and the reference is called a foreign key. 

```ALTER TABLE tblBook ADD CONSTRAINT fk_PubID FOREIGN KEY (PubID) REFERENCES tblPub(ID) ON UPDATE NO ACTION;```

Let's look at our columns again:

```SHOW COLUMNS FROM tblBook;```

You'll notice that the 'Key' column now has 'MUL' for PubID. 
This means that we are using that column as an index as well as the primary key column. 
This new index just happens to be non-unique. 

# Summaries

So now that we have our data in place, let's summarize it a bit. 

```SELECT COUNT(*) FROM tblBook;```

What if we want to see the first ten rows in tblBook?

```SELECT * FROM tblBook ORDER BY Date LIMIT 10;```

Let's look at only books published after 1980;

```SELECT * FROM tblBook WHERE Date > 1980 ORDER BY Date;```

And count them:

```SELECT COUNT(*) FROM tblBook WHERE Date > 1980 ORDER BY Date;```

How about only books published in 1980?

```SELECT * FROM tblBook WHERE Date = 1980 ORDER BY ShelfNumber;```

Let's find out how much our books cost:

```SELECT AVG(RetailPrice) FROM tblBook;```

```SELECT MIN(RetailPrice) FROM tblBook;```

```SELECT MAX(RetailPrice) FROM tblBook;```

Let's summarize all of that together.

`````````sql
SELECT 
AVG(RetailPrice) AS 'Average Price',
MIN(RetailPrice) AS 'Lowest Price',
MAX(RetailPrice) AS 'Highest Price'
FROM tblBook;
`````````

## Make queries using joins

Joins in SQL logic merge two different but related tables together so that the data can be queries across them.{% sidenote 'sqljoins' '"A Visual Explanation of SQL Joins," Coding Horror, 11 October 2007 https://blog.codinghorror.com/a-visual-explanation-of-sql-joins/' %} 
Joins seem complex to think about, but they are really very simple. 
They make sets of data based on conditions.
For our practice data, which deals with book lists, we might want to find books published by certain publishers, which is contained in a different table. 

Here are some examples. 

I want to list out all the books in the list that were published by Oxford University Press. 

```SELECT * FROM tblBook b RIGHT JOIN tblPub p ON b.PubID = p.ID WHERE p.Publisher = 'Oxford University Press';```

How many locations does OUP have? 

```SELECT COUNT(*) FROM tblPub WHERE Publisher = 'Oxford University Press';```

Where are they?

```SELECT * FROM tblPub WHERE Publisher = 'Oxford University Press';```

What if I only want the books published by OUP's US office? 
I have to specify an additional criterion. 

```SELECT * FROM tblBook b RIGHT JOIN tblPub p ON b.PubID = p.ID WHERE p.Publisher = 'Oxford University Press' AND p.Country = 'US';```

I wonder if books cost more from the OUP GB location than from the OUP US location.

```SELECT AVG(RetailPrice) FROM tblBook b RIGHT JOIN tblPub p ON b.PubID = p.ID WHERE p.Publisher = 'Oxford University Press' AND p.Country = 'GB';```

```SELECT AVG(RetailPrice) FROM tblBook b RIGHT JOIN tblPub p ON b.PubID = p.ID WHERE p.Publisher = 'Oxford University Press' AND p.Country = 'US';```

# Output from MySQL queries as views

We can take any of the above queries and output the results to a virtual table called a *view*. 
Views let you create and drop tables on the fly without as much risk of accidentally dropping a real table from your database. 

We need to add ```CREATE VIEW qryName AS``` to the front of any of our query commands. 

Here is an example using our price summary from above:

```CREATE VIEW qryPrices AS SELECT AVG(RetailPrice) AS 'Average Price', MIN(RetailPrice) AS 'Lowest Price', MAX(RetailPrice) AS 'Highest Price' FROM tblBook;```

See if it worked by listing the tables:

```show tables;```

Look at what is in the new table:

```SELECT * FROM qryPrices```

It should match the output from when you ran the query before. 

Try to writes some other views to tables 

## Output from MySQL queries in other formats

We can output all of this stuff outside of our MySQL prompt shell (in a normal shell).

Let's ask for the summary of book prices in HTML and then we can try some other queries if we have time. 

```quit``` to exit the MySQL prompt.

Now you have exited from the MySql prompt.

```mysql -u root -p -H -e "SELECT AVG(RetailPrice) AS 'Average Price', MIN(RetailPrice) AS 'Lowest Price', MAX(RetailPrice) AS 'Highest Price' FROM tblBook;" booksinfo```

# Exporting and Importing 

To export your whole database so that you can use it elsewhere (i.e., transfer it to a different server) do the following command:

```mysqldump -u root -p booksinfo > booksinfo.sql```

If you want to then import that same database somewhere else, the command is very similar. The direction changes, and instead of the specialized ```mysqldump``` command, you use just the standard MySQL client command:

```mysql -u root -p booksinfo < booksinfo.sql```

# MySQL in Bash scripts

I would suggest looking at the the manual page for the MySQL client to see what you can do on the command line.{% sidenote 'mysql-man' '“mysql(1): MySQL Tool.” Linux Man Page. Accessed July 15, 2016. http://linux.die.net/man/1/mysql.' %}

You will be expected in class to be looking up other resources as well. 
If you find something useful, share it with me and I will put links here.

To execute MySQL commands from within BASH (i.e., not logging into MySQL first), you have to use the `-e` switch for "execute," like this:

```mysqldump -u root -p "SHOW DATABASES"```

This will still prompt you for your password. If you want to add the password into the command, you can do it in one of the two following ways:

```mysqldump -u root -p"root" "SHOW DATABASES"```

```mysqldump -u root --password="root" "SHOW DATABASES"```

This will allow you to set the username and password as variables in your scripts and then run commands to work with data inside a database from the script: 

```
#1/bin/bash
# set MySQL credentials
SQLUSER=root
SQLPASS=root
# show all databases 
mysqldump -u SQLUSER --password="$SQLPASS" "SHOW DATABASES"
```

# For Next Time

Next time we are going to begin talking about presentations and creating good presentation materials. 

I would like you to read/deep skim Edward Tufte's piece on the stupidity of PowerPoint.{% sidenote 'powerpoint' 'Tufte, Edward R. The Cognitive Style of Powerpoint: Pitching Out Corrupts Within. Cheshire, Connecticut: Graphics Press, 2011. https://paperpile.com/shared/gQqL5P.' %} 

## Exemplars

I would also like you to view the following video of a talk by Lawrence Lessig.
We will look at parts of this in class as well, but it would be good if you could sit down and view the whole thing over the course of the weekend.
It exists in four parts linked below.

<div class="video-container">
  <iframe width="420" height="315" src="https://www.youtube.com/embed/Qk_5UccWm3o" frameborder="0" allowfullscreen></iframe>
</div>
<div class="video-container">
  <iframe width="420" height="315" src="https://www.youtube.com/embed/piLXKUE_Bzo" frameborder="0" allowfullscreen></iframe>
</div>
<div class="video-container">
  <iframe width="420" height="315" src="https://www.youtube.com/embed/ajv0Lxaqoys" frameborder="0" allowfullscreen></iframe>
</div>
<div class="video-container">
<iframe width="420" height="315" src="https://www.youtube.com/embed/xSbWG2LFrOk" frameborder="0" allowfullscreen></iframe>
</div>

## Reveal.js

We will be using reveal.js to create presentations. 
Please click through this demo presentation and see what is possible to do with it.{% sidenote 'reveal' 'El Hattab, Hakim. Reveal.js: The HTML5 Presentation Framework. http://lab.hakim.se/reveal-js/#/.' %} 
You can also view the source code for the demo presentation. 
We will look at this together in detail. 

## Thought leaders and TED Talks

You should also give the following video a watch.
It will help put into perspective what is really happening when we watch TED Talks and similar presentations. 
Also, it is amusing.

<div class="video-container">
  <iframe width="560" height="315" src="https://www.youtube.com/embed/_ZBKX-6Gz6A" frameborder="0" allowfullscreen></iframe>
</div>
