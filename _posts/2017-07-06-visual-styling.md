---
layout: post
title: "Visual styling for the web"
era: Web 
tags: 
- Jekyll
- CSS
- HTML
- Markdown
category: class
quiz: https://goo.gl/forms/jgNSC296plXYFdrk2
---

For most of class today, we will spend time creating our base site and then exploring ways that we can change and customize the style to our liking. 

We'll learn about CSS and about linking resources so that they show up where we want them. 
<excerpt/>

# Jekyll

Once you have chosen a Jekyll theme for your site, we will need to fork the theme, make appropriate changes to turn it into our own, and then we can get to work on customizing the look and feel of the site. 

When we make changes to Jekyll's configuration, we are ostensibly telling it where to find different necessary files for rendering the site, like our CSS file. 

Let's take a look at different ways of linking. 

# Linking

Linking is what makes the Internet what it is in terms of how information is organized. 
Without links, we would have to know the location of every single thing we wish to get to. 
We would have to index everything: that is, we would need a list. 
Linking allows us to move between resources, call and embed resources within one another, and in some cases find resources based on their relationships. 

### Relative and absolute paths

We have choices about how we can link to resources. 

Let's look at the links in the examples on the last page:

```html
<link rel="stylesheet" href="css/styles.css">
<script src="js/scripts.js"></script>
<img src="images/pretty.img" alt="A pretty picture" />
<a href="index.html" title="Home">Return home.</a>
```

These are all examples of relative paths. 
This means that they assume that the files referenced here are located near our index page. 

If we were to represent the same links with absolute paths, we would have to add the domain name / hostname also. 
See below:

```html
<link rel="stylesheet" href="http://www.somewebsite.com/css/styles.css">
<script src="http://www.somewebsite.com/js/scripts.js"></script>
<img src="http://www.somewebsite.com/images/pretty.img" alt="A pretty picture" />
<a href="http://www.somewebsite.com/index.html" title="Home">Return home.</a>
```

Let's consider the advantages and disadvantages of each of these approaches and ask these questions:

1. What happens if we have to change our doman name or move to a different server?
2. Is there perhaps a way to automate such a change and still provide an absolute path?

Let's move on to working with visual elements.

# CSS

CSS is an acronym for "Cascading Style Sheet."

If HTML is the medium for web content, then CSS is the medium for the visual styling of the web. 
Whenever a website looks like anything other than just a blank page, there is CSS involved. 

We will continue to use a combination of Markdown, HTML5 and CSS3 to construct our very own web pages. 

# Fork

Once you have chosen a Jekyll theme, you will make a copy of it in GitHub on your account. 
We'll use this as an opportunity to get wome web code and see what that looks like. 

You are not committing to anything today: this is just for practice. 
We'll start by going to this repo:

https://github.com/henrythemes/jekyll-starter-theme

This is the repo for a very, very simple Jekyll web theme. 
We will us this as a starter theme to practice with. 

Once you are at the above repo, click the "Fork" button and select your username when prompted to make a copy of the repo in your account.{% marginnote 'fork' '![Click the "fork" button.](/assets/ref-images/fork.png)' %} 

After a few seconds you will be taken to the repo page for the copy that you have made in your account. 

# Configure

Once we have the base theme forked, we need to make sure that the site is going to show up at the right address. 

The address that we want is `http://YOUR-GITHUB-USERNAME.github.io`. This is the default user site address for GitHub pages. 

GH Pages will serve this site from code in the master branch of a repository in your account named the same as the fully qualified domain name (FQDN) or just the full URL to our desired site. 

Therefore, if your GH Pages user site defaults to `http://YOUR-GITHUB-USERNAME.github.io` then we have to make a repository in your account titled `YOUR-GITHUB-USERNAME.github.io`. 
The easiest way to do this is to just change the name of the theme repository that we just forked so that it matches what we need. 

To do this, click the settings tab on your repository page, enter a new name under "Repository name," and then click "Rename."

## \_config.yml

Once we are there, we should be able to look into `_config.yml` file right in GitHub and make sure that our site settings are correct.
We will likely have to change three variables, if they exist: `path`, `url`, and `baseurl`.
These will be different for different themes, so we'll look over this together in class. Basic principles are as follows:

You want `url` to match the desired URL for your site: `http://YOUR-GITHUB-USERNAME.github.io`.

`path` specifies a path where files are held. 
For the GH Pages user site, it needs to have no value. You can either delete that line, comment it, or just put a set of double quotes to specify that Jekyll should not try to rewrite the links and append a subdirectory. It will look like this:

`path: ""`

The same is true for `baseurl`.

All that these do is tell Jekyll where things are when it is trying to build the site. 
Remember, linking is dynamic in the build process, so Jekyll is trying to figure out how to tell your browser where to find stuff that it needs to render the site. 

## Test

Once you have your config set accordingly, then you should be able to look at your site at `http://YOUR-GITHUB-USERNAME.github.io`. 
Don't worry if it doesn't work or if something looks weird. 
Nothing is broken in those cases, you'll just need to troublshoot to figure out what is wrong. This is part of the developmet workflow. 

# Development

A "development workflow" has several stages that happen in order.{% sidenote 'ghflow' '“Understanding the GitHub Flow.” GitHub Guides. Last modified December 12, 2013. https://guides.github.com/introduction/flow/.' %} 
We have been gearing up to think about our work in this context. 

A typical development workflow might conceptually look like this:

1. Create new branch of source code for new feature
2. Work on code for new feature in new branch 
3. Test feature and make fixes if necessary
4. Run with feature in testing environment to ensure that feature works
5. Get feedback about new feature and integrate suggestions if necessary
6. Merge new feature into main workflow
7. New feature is live in production

## Good advice about development and design 

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">&quot;Write the best code possible today and be completely unattached to it and willing to delete it tomorrow.&quot;<a href="https://t.co/mBAJhip0KP">https://t.co/mBAJhip0KP</a></p>&mdash; Adam Wathan (@adamwathan) <a href="https://twitter.com/adamwathan/status/747429538930393088">June 27, 2016</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

# For next time

I want you to continue to work with your site and actually begin creating some content: write a blog post. 

This involves having an idea, making an outline of what you want to say about that idea, committing some text, referencing outside information, and maybe putting a picture in to give a visual anchor to your text.

I would also like you to move through the W3Schools HTML5 and CSS3 tutorials on your own, outside of class.{% sidenote 'css-tutorial' '“HTML Tutorial.” W3Schools. http://www.w3schools.com/html/default.asp.<br/><br/>“CSS Tutorial.” W3Schools. http://www.w3schools.com/css/default.asp.' %}
