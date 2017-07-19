---
layout: post
title: "Spreadsheets and Scripting Data"
era: Data
tags: 
- data
- Bash
- scripting
- spreadsheets
category: class
---

Today we will look at two different ways to handle data:

1. Using a spreadsheet.
2. Writing a script.

Both approaches have their advantages and we will discuss these. 
This is a day when we will talk about what tool is right for what job. 

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

With a partner, I want you to find a script on GitHub or elsewhere and look at how it uses variables. 
You can use the faceted search on GitHub to specify langauge as "Shell" since we are looking for shell scripts. 

Here is a great example of a script that does something seemingly very difficult in a reasonably straightforward manner: http://www.sbprojects.net/projects/raspberrypi/sms.php

We'll look at it together in class and look at the scripts that you found. We will also begin writing our own for the next assignment. 

# For next time

We're going to break into databases next time and have a MySQL crash course. 
I would like you to look over some basic MySQL tutorials on your own so that we are prepared to dig into this.{% sidenote 'sql' 'Sverdlov, Etel. “A Basic MySQL Tutorial.” DigitalOcean. Last modified June 12, 2012. https://www.digitalocean.com/community/tutorials/a-basic-mysql-tutorial.'%} 