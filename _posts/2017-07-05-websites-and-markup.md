---
layout: post
title: "Websites, Markup, and Markdown"
era: Web
tags: 
- websites
- markup
- markdown
- html
- css
category: class
quiz: https://goo.gl/forms/wzMk5jv6FjuQ9WiZ2
---

This week's tasks will involve some very simple coding (markup, really) and continued exploration and use of our system administration skills. 

Last Friday we learned how to set up a very basic website using Jekyll and GitHub pasges. 
This week we will expand on that significantly, learn how to use markup to change the style of our content, and then learn to publish content to the web. 
<excerpt/>

First things first, we need to know some things about markup. 

# Markup and Markdown

Markup has been used over the last several decades to enhance plaintext for web use. 

Today we will consider some of the basics. 

Markdown is a markup language. 
We had a brief introduction to it last week when we established our first repositories on GitHub. 

## Why are we learning Markdown? 

For starters, Markdown is easier to use than HTML or other markup languages. 
It doesn't require complicated tags, which have a high potential for typographical error. 

Jon Mitchell posits the three following good and compelling reasons that everyone should learn Markdown:{% sidenote 'reasons' 'Mitchell, Jon. “3 Reasons Why Everyone Needs to Learn Markdown - ReadWrite.” ReadWrite. Last modified April 17, 2012. http://readwrite.com/2012/04/17/why-you-need-to-learn-markdown/.' %}

1. It is easy to read. 
2. You will make fewer errors.
3. It helps us to get rid of buggy, crashy, loss-prone content management systems (CMS). 

All of the above boils down to a simple comparison that Mitchell makes:

HTML:

```
<h1>Why <em>you</em> should use Markdown to write your next blog post</h1>

<p><a href=”http://daringfireball.net/projects/markdown/”>Markdown</a> is just so dang legible, it will make your <em>whole life</em> easier. <strong>I promise.</strong></p>
```

Markdown:

```
# Why *you* should use Markdown to write your next blog post

[Markdown][1] is just so dang legible, it will make your *whole life* easier. **I promise.**

[1]: http://daringfireball.net/projects/markdown/basics
```

The above examples render the same thing when parsed. Which would you rather use? 

We will go over some of the basics in class today, but I would also like you to review the resources listed here independently, outside of class. {% sidenote 'markdown' '“Mastering Markdown.” GitHub Guides. Last modified January 15, 2014. Accessed June 27, 2016. https://guides.github.com/features/mastering-markdown/.<br/><br/>This guide is oriented toward GitHub, but the skills represented there extend well beyond that context.' %}

We will work interchangeably in HTML and Markdown over the course of this week.

# HTML5

HTML is an initialism for "HyperText Markup Language."

"Hypertext" is text that contains links to other text.{% sidenote 'markup-history' 'Keith, Jeremy. “A Brief History of Markup.” A List Apart 305 (May 4, 2010). http://alistapart.com/article/a-brief-history-of-markup.' %}
The Web, as we know it, relies on hypertext to for us to communicate with systems and with other humans. 
It is the medium of Web content.

HTML5 is the latest iteration of a standard related to the writing of web content.
Web markup has a long history over the last few decades, beginning with Tim Berners-Lee, one of the fathers of the modern web (and the inventor of HTML).
Berners-Lee proposed the creation of an information management system for the European Agency for Nuclear Research (CERN) in the late 1980's.{% sidenote 'html-origin' 'Berners-Lee, Tim. Information Management: A Proposal. European Agency for Nuclear Research (CERN), March 1989. Accessed June 27, 2016. https://www.w3.org/History/1989/proposal.html.' %} 

When we write Markdown and then post it to GitHub, a system actually translates it into HTML5. 

# Hands-on: Write a blog post

Go to https://github.com/inls161/inls161.github.io. 

This is where our class blog files will be stored. This is where you will share resources with the rest of the class. 

In order to share something, you have to create a new post file. When you do this, it will create a new branch and a pull request that sends a message to me. When I get that message, I will approve the file and it will appear on the blog. 

Today, we'll learn how to do this together. 

# For next time

I would like you to look at this tutorial about creating a website using Jekyll and GitHub Pages. 

Clark, Barry. “Build A Blog With Jekyll And GitHub Pages – Smashing Magazine.” Smashing Magazine. Last modified August 1, 2014. https://www.smashingmagazine.com/2014/08/build-blog-jekyll-github-pages/.

We have already done this in a very rudimentary way, but we will do it again to create a better final product. 

Please also look at these themes and choose one for your site. Some have dynamic navigation (those are listed first == easy). You will modify them heavily. 

## Some easy themes

http://jekyllthemes.org/themes/basic/

http://jekyllthemes.org/themes/trading/

http://jekyllthemes.org/themes/devjournal/

http://jekyllthemes.org/themes/gravity/

## More challenging themes

http://jekyllthemes.org/themes/jekyll-clean/

http://jekyllthemes.org/themes/thinkspace/

http://jekyllthemes.org/themes/vitae/

http://jekyllthemes.org/themes/dbyll/

http://jekyllthemes.org/themes/blackdoc/

http://jekyllthemes.org/themes/daktilo/