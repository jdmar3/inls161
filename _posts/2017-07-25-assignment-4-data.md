---
layout: post
title: "Assignment #4: Collect Data and Make a Database"
era: Data
short_description: "Write a script to collect and manipulate data and interact with a database"
percentage: "15"
category: assignments
start_date: "2017-07-25 23:59"
---

For this assignment, you will write a bash script to prompt a user for input, collect responses, and manipulate those responses into a structured data format. Then you will enhance it with the ability to interact with a database. 

This assignment aims at strengthening our scripting skills and learning how to create a well-formed dataset to work with. 

You will create a short questionnaire and then use Bash to script collection of answers, write them to a temp file and then import the data in that temp file into a database.

<excerpt/>

## Skillsets

You will be exposed to the following skillsets;

1. Scripting user input
2. Saving data to csv file
3. Writing to temporary files
4. Scripting database interface

## Expectations

I expect you to create two scripts 
1. One that will take input from users and then store their responses to a CSV file. It must aggregate the responses of multiple users and therefore needs to have some form of disambiguation involved in the data generation process. 
2. A second script that will allow you to write the information gathered into a MySQL database instead of into a CSV file as the final output form. 

## Prerequisites

The only thing that you will need is Bash and text files, and MySQL, all of which are available in CodeAnywhere (you can use the MySQL stack to start your project).

## Instructions

You will need to do the following for this assignment to be considered complete. 

1. Fork this repository: https://github.com/inls161/task-4-data
2. Clone it to your CodeAnywhere container.
1. Create a list of five survey-type questions.
2. Write a script that will do the following:
  1. Ask each question of the user running the script.
  2. Write a random string of characters to a variable as a unique identifier.
  3. Write the datestamp to a variable.
  4. Accept text input from the user and write each answer as a variable.
  5. Save all answers and other data to a CSV file.
3. Create a database that has the appropriate variables and variable types (NB: You can script this: it might be an accessory script or a conditional statement in your script).
4. Write a script to write your data into a MySQL database (you can call this script from your other one, or vice versa):
  1. connect to a MySQL database (HINT: this will involve setting variables for MySQL USERNAME, PASSWORD, and LOCATION)
  2. enter the data input by users into a MySQL database 
  3. dump the MySQL database into a .sql file in your repository directory with the rest of your files after it has been modified with new data (IMPORTANT: make sure the filename has a timestamp)
5. Collect some data from your peers: collect at least 5 responses to your survey. Each time someone new takes, the script should add a response to your database.
5. Write a blog post that links to your fork of the repository and write a brief explanation of what your scripts actually do. 