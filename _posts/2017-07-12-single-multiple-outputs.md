---
layout: post
title: "Single input, multiple outputs"
era: Text
tags: 
- pandoc
- text
- conversion
- LaTeX
category: class
---

We will spend today exploring making different types of output from a single input file. 
There are many advantages to this approach to creating files:

1. You only have to change one source file.
2. No need to worry about conflicting information resulting from changes made in one file but not another.
3. The hierarchy of headers (i.e. the document structure) is easy to read. This structure persists across conversion to different types.
4. Source to multiple outputs is easily automated. 

We will pay a lot of attention to automation this week.

<excerpt/>

We've briefly discussed Pandoc now. 
It bills itself as the "Universal Document Converter." 
This is reasonably true, but it might require some creative combinations of switches within Pandoc commands as well as multiple commands strung together or intermediate commands to get the desired output. 

The benefit of troubleshooting and understanding this process is that once we do, we can more easily optimize our conversions and automate them. 
We'll talk more about this as we go forward. 

# Source to output conversion

It is possible to use GUI tools to create and convert documents. 
Support is somewhat limited, but in LibreOffice, we can at least create a PDF from our ODT and DOCX files. 

We can also manipulate the styles of the headers and other structural elements that we have assigned using Markdown in our GUI editors. 

One convenient effect of starting with plaintext marked up with Markdown is that we have those structural elements when we convert them into another format and then edit them elsewhere. It is certainly possible to start in the GUI editor and define the same things, but after becoming acquainted with Markdown, it should feel somewhat more burdensome to use the GUI. Arguably, it is. There is a great deal more that goes into a DOCX or an ODT file, structurally, than in a plaintext file with Markdown in it. 

We also have the disadvantage of only being able to operate on those GUI-created files in limited ways on headless or remote systems. 

If we keep plaintext at the core of our workflows and GUI editors toward the periphery, we will be served in the end as we will always have access to our work, on any system, without any huge barriers to editing and changing. 

## Commands

We're going to practice some conversions using Pandoc today. We will also work in groups. 

First, we need to get some files. 

Fork and clone this repository into your CodeAnywhere container:

`https://github.com/inls161/pandoc-practice`

Once you have the files in your CodeAnywhere container, I will show you some things in class and then in your groups you will answer and mark up the `example.md` file using the instructions in the file. 

***When you are finished with the questions in file:*** 

1. I want you to change the name of the file to your GitHub username. 
2. You will then work as a group to convert the file to HTML, DOCX, and ODT formats, per the instructions in class. I also want you to open the files on your lab computers so you can see what you have done. 
3. Then I want you to add, commit, and push your changes. 
4. Finally, you will create a pull request in GitHub to get these files back into my original repository.  

## Basic Pandoc commands

{% marginnote 'pandoc-commands' 'All Pandoc commands are documented here: http://pandoc.org/README.html<br/><br/>A good set of example commands exists here: http://pandoc.org/demos.html' %}

Convert a Markdown file to HTML:

`pandoc -o example.html example.md`

Pandoc reads the filetype from the extension in normal usage. 
If you want to convert a file directly from a URL, you will have to specify the filetype, like this:

`pandoc -f html -t markdown http://inls161.johndmart.in/syllabus/`

You can make sure that certain things, like quotes and em-dashes, get read and formatted propery by specifying the "Smart" switch (a capital `-S` or `--smart`):

`pandoc -S -o example.html example.md`

There are a host of other commands in the documentation. Be sure to try them out. 

## Specific file commands

Convert your markdown to HTML:

`pandoc -o example.html exampld.md`

If you wish to convert to a DOCX or ODT file:

`pandoc -o example.docx example.md`

`pandoc -o example.odt example.md`

If you wish to convert between two different word processor filetypes, we might have to get a little creative. 
We learned in class that if we issue the following command, we get errors related to file encoding and the conversion will not work. 

`pandoc -o example.docx example.odt`

If, however, we add an intermediary step, say through HTML, we can get the output that we want. Try it like this instead: 

`pandoc -o example.docx example-tmp.html && pandoc -o example.odt example-tmp.html`

This preserves the formatting and extracts the text from the DOCX as an HTML file and then converts that HTML into ODT. 
We do not have the weird encoding errors this way, and we don't have to mess with pipes. 

Filter a document through a template file:

`pandoc -S --reference-docx=FILE -o example.docx example.md` 

In the above command, you need to specify the location of the template file. 
If it is a file called `template.docx` and is located in the same directory as your Markdown source, then the command will be:

`pandoc -S --reference-docx=./template.docx -o example.docx example.md`

You can also use an ODT or OTT for reference:

`pandoc -S --reference-odt=./template.ott -o example.odt example.md`

# For tomorrow

Tomorrow, we are going to learn one more output format and then learn how to script all of our outputs together so that we can save ourselves time. 

I would like you to go through the Writing Shell Scripts tutorial by William Shotts for tomorrow.{% sidenote 'shell-scripts' 'Shotts, William, Jr. “Writing Shell Scripts.” LinuxCommand.org. http://linuxcommand.org/lc3_writing_shell_scripts.php.' %} 
This will show you the basics of scripting. 
The scripts that we will write will be very, very simple, but it is good to have looked over this before we start. 