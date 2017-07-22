---
layout: post
title: "Scripting Data Cleaning"
era: Data
tags: 
- data
- Bash
- scripting
- spreadsheets
category: class
quiz: https://goo.gl/forms/BmYowGVGEeLYdmQC3
---

Today we will look at two different ways to handle data:

1. Writing a script.
2. Using a spreadsheet.

Both approaches have their advantages and we will discuss these. 
This is a day when we will talk about what tool is right for what job. 

<excerpt/>

Spreadsheets are very good as calculators. 
In fact, that is what they are designed to do. 
All other uses for spreadsheets are adaptations and should be used with caution.

Scripts are sets of instructions that you can use replicate and automate tasks. 
That is their only real purpose. 
They can be adapted to other purposes as well: perhaps become a rudimentary interface, for instance.

## CSV to spreadsheet

Spreadsheets appear to operate in a very simple manner, storing data in rows and columns just like any other table, but looks can be deceiving.{% marginnote 'spreadsheet' ''%} 

Just like with DOCX and ODT files when compared with plaintext files, spreadsheets hide a lot of metadata underneath what appears on the surface. 

Unlike with the relationship between plaintext and interface-wrapped formatted text files, it is more difficult to get all of the information out of the spreadsheet. 

As mentioned in the piece by Paul Ford, spreadsheets can hide a lot of things from us, including errors. 
If our code to perform the same kinds of operations is visible to us, it is easier to check for errors. 

That said, spreadsheets are a powerful tool and should be used in certain tasks in preference over other tools. 

Once you have learned to do basic math in a spreadsheet, there is absolutely no reason to ever use a calculator (or calculator app) for instance.

## Caveats and pitfalls of using spreadsheets

This forum post is a good guide to things that you should be aware of when using spreadsheets:

https://forum.openoffice.org/en/forum/viewtopic.php?t=39529

It pertains to OpenOffice, which is the productivity suite that LibreOffice was forked from some years ago. 
OpenOffice is now owned by Oracle and some of the community was not happy with licensing changes that had occured, so they jumped ship and moved their development to LibreOffice under the umbrella of the Open Document Foundation. 
The software still operates similarly enough that the information is relevant to us. 
This is because both suites use ODF at their core. 

It will also be a good idea to have a look at the LibreOffice documentation to familiarize yourself with it as a reference: https://www.libreoffice.org/get-help/documentation/

Finally, here is a compendium of all of the functions available to you in LibreOffice Calc: https://help.libreoffice.org/Calc/Spreadsheet_Functions

# Scripting data collection and handling

Your next assignment is to collect data and store it using a BASH script. 

Today we will look at how you can write scripts that take user input and write that input to a CSV file. 

For starters, we need to look more closely at variables. 

## In-class exercise

Today we cleaned and compiled the data that we generated earlier in the week. 
Instead of doing this in a spreadsheet, we wrote a script that would handle all of the necessary changes, write a new file with a header row of variable names, and then cleaned up temporary files created in the process. 
We did all of this without ever overwriting our original files. 

### Why did this work? 

A BASH script (or any script) is a set of instructions. 
In the case of BASH, the instructions are the same as the commands that we can put right into the terminal.
So anything that we can do in a terminal, we can do in a script, meaning that we can automate any process that we can run in the terminal. 

You can view the script and look at the comments which explain step by step what the script does. It is linked here: https://github.com/jdmar3/data-practice

```

#!/bin/bash
#############################################################################
# This script cleans and compiles the data that we collected in class this
# week without ever actually opening or operating on the files themselves.
# In this form, it only operates on the CSV files, but could easily be 
# modified to handle other types. 
# 
# The script also adds a header row to the file with names for the variables.
#############################################################################

# specify temp directory variable
TEMPDIR="./temp"
# specify names of variables in a CSV list
VARNAMES="ghusername,heightcm,wakeuptime,semestersleft,distancefromhome"
# make temp directory
mkdir $TEMPDIR/
# copy all CSV files into temp directory
cp ./CSV/*.csv $TEMPDIR/
# convert sepideharc.csv to csv
cp $TEMPDIR/sepideharc.csv $TEMPDIR/sepideharc.csv.bck
paste -d, -s $TEMPDIR/sepideharc.csv > $TEMPDIR/sepideharc.csv.tmp
cp $TEMPDIR/sepideharc.csv.tmp $TEMPDIR/sepideharc.csv
# replace pipes in shantank03.csv with commas
cp $TEMPDIR/shantank03.csv $TEMPDIR/shantank03.csv.bck
tr "|" "," < $TEMPDIR/shantank03.csv > $TEMPDIR/shantank03.csv.tmp
cp $TEMPDIR/shantank03.csv.tmp $TEMPDIR/shantank03.csv
# replace double comma in jdmar3.csv with single commas
cp $TEMPDIR/jdmar3.csv $TEMPDIR/jdmar3.csv.bck
tr ",," "," < $TEMPDIR/jdmar3.csv > $TEMPDIR/jdmar3.csv.tmp
cp $TEMPDIR/jdmar3.csv.tmp $TEMPDIR/jdmar3.csv
# reformat time in marhass.csv
cp $TEMPDIR/marhass.csv $TEMPDIR/marhass.csv.bck
sed 's/,0645,/,06:45,/g' $TEMPDIR/marhass.csv > $TEMPDIR/marhass.csv.tmp
cp $TEMPDIR/marhass.csv.tmp $TEMPDIR/marhass.csv
# Create a new csv with variables in a header row
echo "$VARNAMES" > $TEMPDIR/00varheader.csv
# concatenate all data
cat $TEMPDIR/*.csv > ./`date --iso-8601`-class-data-compiled.csv
# clean up temp files
rm -r $TEMPDIR

```

You should clone the repository and run the script to see what it does. 

# For next time

We're going to break into databases next time and have a MySQL crash course. 
I would like you to look over some basic MySQL tutorials on your own so that we are prepared to dig into this.{% sidenote 'sql' 'Sverdlov, Etel. “A Basic MySQL Tutorial.” DigitalOcean. Last modified June 12, 2012. https://www.digitalocean.com/community/tutorials/a-basic-mysql-tutorial.'%} 