---
title:  "Got git, GitHub, Ruby, and Jekyll"
date:   2021-03-10T16:22:00-0500
categories: 
  - mm jekyll
tags:
  - github 
  - jekyll 
  - ruby
  - minimal mistakes
excerpt: "Getting things ready to use GitHub, GitHub Pages, Jekyll, and Minimal Mistakes theme, and building a basic site."
toc: true
toc_label: Contents"
---

*March 10, 2021*

> <span style="color: #596275">A simple walkthrough of setting up a GitHub account, installing GitHub Pages, Ruby, Jekyll, and Minimal Mistakes, and standing up a basic site.</span>


If you already know your way around **git** and **GitHub**, then you can jump to the [Install Ruby](#install-ruby) section; if not it may be useful to go through this part.

I went through this process using macOS, and so any code or steps I discuss are specific to macOS.

## git and GitHub before GitHub Pages
Change is inevitable in software code, documentation, reports, presentations, and other material. Version control is what let's us keep track of changes. 

[git](https://git-scm.com/) is an open-source version control system that keeps revisions organized and easily accessible and allows collaboration between multiple developers or authors, and even enables non-collaborators to view and download files. While git is a command line tool, [GitHub][] is a git repository hosting service –– the central hub where developers store and share project, code, documentation, and other material and interact with other developers. That makes GitHub something like the equivalent of a social networking site for programmers.

## GitHub Pages
So, you can store (host) and version files on GitHub. Normally, this is storing and versioning of code and documentation. [GitHub Pages][] is a free place (built into GitHub) to store files that provide a way for the user to host a personal website (user website) and websites for the user's projects / repositories. These can be direct HTML files that you can simply view like a website; or other types of files that can be run through a converter or templating tool such as Jekyll and transformed into HTML so that they can be viewed like a website.

> GitHub Pages is a static site hosting service that takes HTML, CSS, and JavaScript files straight from a repository on GitHub, optionally runs the files through a build process, and publishes a website. –– *from [GitHub Pages documentation](https://docs.github.com/en/github/working-with-github-pages/about-github-pages)* 

For each registered GitHub account you are allowed:

- _one_ personal **User Page** (which will have the domain name `https://your-username.github.io`) and
- _unlimited_ **Project pages** (which will have the domain name `https://your-username.github.io/your-repo-name/`)

`your-username` is your GitHub user name and `your-repo-name` is the name of your GitHub repository.

**Note** You can set up custom domains but I won't be discussing it here.
{: .notice--info}

### User (Personal) Page
To host a User Page, you first have to create a repository named **your-username.github.io** (it has to be named exactly in this format; anything else will not work!). This is the repository that will house all the files in the `master` branch that will be used to build your website.

### Project Page
To build a Project Page, you have to create a project (repository). The project can be named anything you'd like, say **sampleproject**. The files used to build the website for **sampleproject** have to be housed in the `gh-pages` branch. 

**Note** User Page uses the `master` branch but Project Page uses the `gh-pages` branch for storing the files used to build the website.
{: .notice--info}

**Note** To have Project Page you don't need a User Page first (if you don't want to have one). However, the final URL for the project website will still be `https://your-username.github.io/sampleproject/`.
{: .notice--info}


In my case, my GitHub user name is **`niimmiish`**. So, for my: 

- Personal website
	- my repository is named `niimmiish.github.io` and the site sits in the `master` branch
- Project specific website
	- a project repository (as an example) could be named `mysampleproject` and would be located at `https://github.com/niimmiish/mysampleproject` and the site sits in the `gh-pages` branch


## Getting started with GitHub for the first time
The GitHub site has very [good documentation explaining how to get started](https://docs.github.com/en/github/getting-started-with-github/set-up-git). And here are some helpful [guides](https://guides.github.com/activities/hello-world/).

So, if you don't already have a GitHub account, you need to create one to eventually host your site (for free). 

1. Go to [GitHub.com][GitHub].
2. Click on "Sign Up" to create a new account. Remember, the user name you select is what others on the site will see and will be part of your URL `https://yourusername.github.io`.


## Order of things
There are a couple of ways you can approach how your build out your site. You can either:

- create your repository first on GitHub (if using a Jekyll theme, then fork the theme's repository to create your own repository), then clone it locally on your computer, then develop it locally, and then push it back to GitHub, or
- start locally on your computer, develop locally, and then push it to GitHub.

I used the second approach and will describe that here. The first one is pretty similar, except that you start with a repository on GitHub.


## Install GitHub Desktop app
You can choose to use git on the command line or the visual tool GitHub Desktop app – it's just personal preference and what you find easier. I used GitHub Desktop for building my website.

1. Download and install GitHub Desktop from the [GitHub Desktop site](https://desktop.github.com/).
2. Launch GitHub Desktop and enter your username and password for the GitHub.com account you created in the previous step. (Enter name and email you want viewable publicly).
3. We don't need to select any repositories at this time. We will do this later (because we are going to initialize and build the site locally first).

## Install Ruby
Jekyll is a Ruby [gem](https://rubygems.org). So, you have to install Ruby first following the directions [here](https://jekyllrb.com/docs/installation/).

## Install Jekyll
You can now install Jekyll with the following command in Terminal.

`$ gem install --user-install bundler jekyll`

This command installs the latest version of Jekyll (in my case it installed Jekyll 4.2.0)

You can find detailed instructions [here](https://jekyllrb.com/docs/installation/macos/#install-jekyll).

## Getting started with Jekyll
As I mentioned previously, there are a couple of ways to get started once you have Jekyll installed on your computer.

1. Clone a Jekyll theme from GitHub to your local computer, then build and serve it locally using `bundle exec jekyll serve`
2. Install a new site structure (scaffolding) using the command `jekyll new`, then build and serve it locally using `bundle exec jekyll serve`, or

I used the second option, which I'll describe next.

## Folder set up
Now that we have everything installed, you first need to create a folder with the files that will make up your website. 

1. I created a folder *ghdocs* in my home folder for developing my personal site. You may choose a different folder name or have it elsewhere.

2. Then navigate to the *ghdocs* folder. In the *ghdocs* folder I created a new site structure with the following Jekyll command.

``` 
$ jekyll new niimmiish.github.io
```

This tells Jekyll to create the new site structure with the necessary files in the folder *ghdocs/niimmiish.github.io*. 

Remember for your User Page to work your GitHub repository must be named using the format **your-username.github.io**. This is why my folder is named *niimmiish.github.io*, which will eventually be pushed to GitHub to the repository **niimmiish.github.io**.

## Installing Minimal Mistakes
The best way to start with and install [Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/) is to use the great [Quick-Start guide](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/), following which you should be able to set up a basic site with some content.

I used the *Gem-based method* and the *Starting with `jekyll new`* sections.

1. In Terminal, navigate to *ghdocs/niimmiish.github.io*
2. Install Gem-based theme by adding the following line to the `Gemfile` (it will be in the newly created *niimmiish.github.io* folder:

	```
	gem "minimal-mistakes-jekyll"
	```

3. Run the following command to fetch and update the bundled gems.

	```
	bundle
	``` 

4. Now you have to configure the site to use the Minimal Mistakes theme. To do this, you have to set the theme in your project’s `_config.yml` file. But first you need to replace the `_config.yml` with the default one from the Minimal Mistakes theme. You can copy the Minimal Mistakes default [`_config.yml`](https://raw.githubusercontent.com/mmistakes/minimal-mistakes/master/_config.yml) from the Minimal Mistakes Quick-Start Guide section [Starting Fresh](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/#starting-fresh).

	Now, set the theme in the newly copied `_config.yml` (you may just have to uncomment the line).

	```
	theme: minimal-mistakes-jekyll
	```

5. Edit `_config.yml` by following the documentation and to suit your needs.

6. Back in Terminal (in *niimmiish.github.io* folder), update the theme with the following command:

	```
	bundle update.
	```

7. Now, you have to tell Jekyll to serve the site so that you can view it locally. Run the following command.

	```
	$ bundle exec jekyll serve
	```

	This is the command that you run to view your website locally. When you run this command, the process does not run to completion but keeps watching for changes to the files in the directory (such as your edits to your site pages or posts), and makes them available when you refresh your browser. The only file it doesn't refresh while running is the `_config.yml` file –– the site conifguration file. You have to stop and restart the website to see any changes you make to this file (this is because it can get very tricky to handle configuration changes while a website is running).
	
	Agggghhh!!!....you get an **error** and you throw your hands up thinking THIS IS NEVER GOING TO WORK! But don't smash that computer just yet!

	There is a dependency missing –– a gem called `webrick` that is required for Jekyll 4.0 –– (which I dont't really understand and don't know enough about to explain). Run the following command in Terminal in *niimmiish.github.io* folder to add it.

	```
	$ bundle add webrick
	```
	
	It will now appear in your Gemfile.

	Run `bundle exec jekyll serve` again. **YES!!! It works now!** 

8. Start up a browser, go to [http://127.0.0.1:4000/](http://127.0.0.1:4000/) and you can view your site locally.

## Adding content
Now you can author content using [kramdown](https://kramdown.gettalong.org) (a pure-Ruby Markdown-superset converter), which is the deafult Markdown renderer for Jekyll. Follow the detailed [Minimal Mistakes documentation][mm] to build out various pages and posts to your liking.

For reference, you can always inspect the source code for my website in the `Gemfile`, or `_config.yml`, or anything  else.

Feel free to let me know about anything I have misstated or comments you have. 

<!------------------------------- FOOTER --------------------------------->

[GitHub]: https://github.com
[Jekyll]: https://jekyllrb.com/
[GitHub Pages]: https://pages.github.com/
[mm]: https://mmistakes.github.io/minimal-mistakes/

