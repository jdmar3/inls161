---
layout: post
title: "Assignment #3: Text Conversion"
era: Text
short_description: "Write a script to convert text files"
percentage: "10"
category: assignments
start_date: "2017-07-17 23:59"
---

This assignment aims to teach you how to use scripted programs to convert marked-up document source files into multiple output formats. 
Its larger purpose is to demonstrate that you can automate your workflows so that you will save yourself time and energy in creating documents for your courses or work going forward. 
This assignment is also intended to show you that you do not need to have expensive software suites in order to produce high-quality, well-formed documents. 

We will use Pandoc, TeXLive, and Bash scripts to complete this assignment. You will write a bash script to convert text files written in Markdown into other formats, such as DOCX, HTML, and PDF. 

<excerpt/>

## Skillsets

You will be exposed to the following skillsets;

1. Converting between document types (Pandoc)
2. Tweaking and fixing markup (Markdown, Pandoc, and TeXLive)
3. Installing software (Linux, Apt)
4. Writing a script to automate multiple outputs from source files (Bash)

## Expectations

I expect you to create a set of well-formed documents which contain original content (i.e. - your own writing). 
You will create multiple document types from a markdown source file. 
The markdown source file will contain a piece of writing that you have done for another class or an original piece for this class.

## Prerequisites

You will need to have Pandoc and TeXLive installed on your CodeAnywhere containers. 
Pandoc can convert most input formats to most other output formats on its own. 
Pandoc uses TeXLive to produce PDFs, so we have to install this in order  to fulfill one of the targets of the assignment. 

## Instructions

You will need to do the following for this assignment to be considered complete. 

1. Fork [this repository])(https://github.com/inls161/convert-documents) into your GitHub account and rename it like this `YOURGITHUBUSERNAME-convert-documents`, Then clone it into your CodeAnywhere container.
3. Rename the script `convert-docs.sh`, contained in this repository, to `YOURGITHUBUSERNAME-convert-docs.sh`. 
2. Edit the script (which has only comments currently) to include commands and make sure that it can be executed. 
3. In your script, you need to include the following output formats:
  - DOCX
  - ODT
  - HTML
  - PDF
  - One other format of your choosing
4. Include some commands to tell the user of the script what is happening while it is working. This will mean sending text to STDOUT and running other commands as part of the script that show the user what they are doing. 
4. Place a markdown version of a piece of original writing into your forked repository. This writing can be a poem, a short story, an essay: anything you wan, as long as it has some structure that can be marked up using Markdown. 
5. Test, tweak and then run your script to produce the four output formats listed above. 
5. Add, commit, and push all of your changes.
6. Once you are satisfied with your outputs, create a new blog post on your website and include the following:
  - A brief description (abstract) of your written work
  - A description of what you did to get it into multiple formats
  - Links to all of your source and output files, and your script. You can link to the repository page if you like, but I would like you to make a list of the files in your blog post.