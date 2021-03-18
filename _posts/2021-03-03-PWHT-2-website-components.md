---
title:  "What's a static site generator and what to do with it?"
date:   2021-03-03T17:40:00-0500
categories: 
  - mm jekyll
tags:
  - jekyll
excerpt: "Reviewing the attractiveness of a static site generator like Jekyll."
---

*March 3, 2021*

> <span style="color: #596275">A simple review of static v. dynamic websites, attractiveness of a static site generator like Jekyll and using a Jekyll theme to host a website on GitHub Pages.</span>

To get started building my website, I had to first understand conceptually static websites and the role of static site generators. Learning about [Jekyll][], one of the most popular static site generators, meant I had to  understand a little about Ruby (at least enough to be able to install it so as to then work with Jekyll). And then, I had to understand how GitHub Pages work.

So, this post is my attempt to explain these concepts, ending with the selection of the [Minimal Mistakes theme][mm] for building my website.

As always, feel free to leave me comments if I have misstated anything or just feedback. 

Here goes...

## What is a static site?
A **dynamic** website, as the name implies, is interactive and constantly changing. Such sites contain server-side and client-side scripting and HTML and CSS and other code such as Java, PHP and more. Examples are websites built and managed with a database-driven CMS (content management system) such as Wordpress, Drupal, etc. For instance, when you search a retailer's website for a product, the results returned are dependent on your search criteria, your location, and other factors i.e., the page doesn't already exist but has to be generated specifically for you. Basically, a lot of components and complexity for added functionality.

A **static** website, on the other hand, contains stationary information, presented in the browser just as it is stored in the source files, coded in HTML and CSS. Such a website shows the same information to every user as the underlying content already exists and is not subject to change based on the user. Any information updated on the website must be made by adding or updating content manually by the website owner.

## Static site generator
A **static site generator** builds a (static) website with plain HTML files. A static site generator is a software application that reads a set of source files (raw text files in various formats residing in a file system and templates) and uses a conversion process to generate ready-to-publish HTML files that can be served by a web server. Templates are reusable components used in web development for repeated formatting or information.

So, a static site generator is basically a script that takes input in the form of content, data, and templates, applies transformations, and generates resulting output as HTML pages. Pretty neat, right!

## So what's the attraction?
I know next to nothing about web development. Just the thought of developing a website conjures up (painful!) images of extensive coding and management.

The painful parts (for me) about developing a website are:

- Learning and fumbling through extensive HTML, CSS, and other coding
- Selecting a hosting service (and possibly incurring hosting costs)
- Managing content and security on the site

A static site generator simplifies this process with the main advantages being:

- Speed: fast website as it is only reading HTML
- Security: don't have to worry about server side attacks
- Simplicity: no database to mangage, only need very basic HTML and CSS knowledge
- Flexibility: develop and run locally, know exactly how it works
- Versioning: use version control software to track changes to the site, merge content from different authors
- Ease of use: get started quickly, use templates for repeated tasks (header, footer, etc.), really understand the different pieces of your website, customize look-and-feel without excessive programming


## Enter Jekyll, Ruby, and GitHub Pages
I found out quickly that [Jekyll][] is an extermely popular static site generator. Jekyll is built with the [Ruby](https://www.ruby-lang.org/en/) programming language. Tom Preston-Werner, co-founder of [GitHub](https://github.com), developed Jekyll as an open source program. Jekyll is the engine behind [GitHub Pages][], which allows you to host a site from your GitHub repository. So, you guessed it -- I am going to talk about this trifecta: GitHub Pages, Ruby, and Jekyll. 


## Jekyll
GitHub Pages doesn't "run" websites. We have to provide static HTML files so that the website can be viewed. This is where Jekyll comes in.

Jekyll is a Ruby [gem](https://rubygems.org) and is what helps you create a static website (a Ruby gem is a library of packaged Ruby code that can be used without explicity writing out that gem's code). Jekyll takes page templates––things like footers, headers, etc. that should be shared across pages of the site (instead of tediously writing out the HTML for each page)––and combines then with other files (blog pages, about page, contact page, etc.) to generate final HTML pages for the end user to see.

I started by reviewing the [Quickstart](https://jekyllrb.com/docs/) documentation on the Jekyll website. While the Jekyll documentation is good, it isn't always easy to follow without a web development background. But the power of open source is that you can find others who shared their experiences to learn from.

Jekyll is really cool to work with. It processes content written in Markdown files to build the website. Markdown is much much easier to work with than HTML with its tags and syntax. Jekyll is GitHub friendly, so once you have the files in your GitHub repository, GitHub will build the website. 

## Selecting a theme
I really wanted to keep things simple and definitely not get into the weeds of coding the appearance and navigation of my site. The very point of using a static site generator like Jekyll is to use a ready theme that can be customized to whatever degree you like and keep evolving it based on your comfort level. I briefly looked through [jekyllthemes.org](http://jekyllthemes.org/) but soon got overwhlemed. But reading through several posts about static sites, I selected the absolutely fabulous, highly configurable, and excellently documented [Minimal Mistakes theme by Michael Rose][mm].

## Next up
Here is the **high-level view of what we are going to cover**:

- Create a [GitHub][] account
- Install [GitHub Desktop](https://desktop.github.com/)
- Install [Ruby and Jekyll](https://jekyllrb.com/docs/installation/)
- Set up the [Minimal Mistakes][mm] theme for the site
- Create content in [Markdown](https://www.markdownguide.org)
- Deploy to [GitHub Pages][]

Feel free to let me know about anything I have misstated or comments you have.

**Read Next:** [Got git, GitHub, Ruby, and Jekyll]({{ site.url }}/mm%20jekyll/PWHT-3-gotgitjekyll/)


<!------------------------------- FOOTER --------------------------------->

[GitHub]: https://github.com
[Jekyll]: https://jekyllrb.com/
[GitHub Pages]: https://pages.github.com/
[mm]: https://mmistakes.github.io/minimal-mistakes/