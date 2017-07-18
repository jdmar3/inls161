---
layout: post
title: "Data cleaning and spreadsheet software"
era: Data
tags: 
- CSV
- data
- spreadsheets
category: class
---

Today we're going to look at one common way of manipulating CSV and other flat data files. 
We'll look at a few more command line tools to do help us, and review how `paste` works once again. 

Then we will look at the result of a compiled CSV file in a GUI environment, to be able to better understand what we're doing in the command line. 
<excerpt/>

# Concatenate and Translate

# Editing on the command line

# CSV to spreadsheet

Spreadsheets appear to operate in a very simple manner, storing data in rows and columns just like any other table, but looks can be deceiving. 

Just like with DOCX and ODT files when compared with plaintext files, spreadsheets hide a lot of metadata underneath what appears on the surface. 

Unlike with the relationship between plaintext and interface-wrapped formatted text files, it is more difficult to get all of the information out of the spreadsheet. 

As mentioned in the piece by Paul Ford, spreadsheets can hide a lot of things from us, including errors. 
If our code to perform the same kinds of operations is visible to us, it is easier to check for errors. 

That said, spreadsheets are a powerful tool and should be used in certain tasks in preference over other tools. 

Once you have learned to do basic math in a spreadsheet, there is absolutely no reason to ever use a calculator (or calculator app) for instance.

# Caveats and pitfalls of using spreadsheets

This forum post is a good guide to things that you should be aware of when using spreadsheets:

https://forum.openoffice.org/en/forum/viewtopic.php?t=39529

It pertains to OpenOffice, which is the productivity suite that LibreOffice was forked from some years ago. 
OpenOffice is now owned by Oracle and some of the community was not happy with licensing changes that had occured, so they jumped ship and moved their development to LibreOffice under the umbrella of the Open Document Foundation. 
The software still operates similarly enough that the information is relevant to us. 
This is because both suites use ODF at their core. 

It will also be a good idea to have a look at the LibreOffice documentation to familiarize yourself with it as a reference: https://www.libreoffice.org/get-help/documentation/

Finally, here is a compendium of all of the functions available to you in LibreOffice Calc: https://help.libreoffice.org/Calc/Spreadsheet_Functions

# For next time

We're going to break into databases next time and have a MySQL crash course. 
I would like you to look over some basic MySQL tutorials on your own so that we are prepared to dig into this.{% sidenote 'sql' 'Sverdlov, Etel. “A Basic MySQL Tutorial.” DigitalOcean. Last modified June 12, 2012. https://www.digitalocean.com/community/tutorials/a-basic-mysql-tutorial.'%} 