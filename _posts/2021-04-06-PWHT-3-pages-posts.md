---
title:  "Personal Website – Part 3: How to create pages and posts"
date:   2021-04-07T12:30:00-0500
show_date: true
last_modified_at: 2021-04-28
categories:
  - personal website
tags:
  - jekyll
  - github
  - posts
excerpt: "Steps to get started with pages and posts."
---

> <span style="color: #596275">A brief explainer about creating content for your website.</span>

**In this series:**<br>
Part 1: [What's a static site generator and what to do with it?]({{ site.baseurl }}/personal website/PWHT-1-website-components/){: style="color: #4b6584"}<br>
Part 2: [Got git, GitHub, Ruby, and Jekyll]({{ site.baseurl }}/personal website/PWHT-2-gotgitjekyll/){: style="color: #4b6584"}<br>
Part 3: [How to create pages and posts]({{ site.baseurl }}/personal website/PWHT-3-pages-posts/){: style="color: #4b6584"} (*You are here*)<br>
Part 4: [Theme customization]({{ site.baseurl }}/personal website/PWHT-4-customization/){: style="color: #4b6584"}
{: .notice.info}
{: style="background-color: #dcdde1"}

This website is built with Jekyll and the Minimal Mistakes theme, and I host it on GitHub Pages. I author content in Markdown and incrementally build and test the site locally. Once I am satisfied, I push the changes to my GitHub repository, where the site is rebuilt and the changes are live.

So how do you create and organize the content for the site?


## Where do I click?
A visitor to your website needs to find their way around — these are the site navigation links, where each link leads to specific content such as **About**, **Blogs**, **Contact**, and so on.

Depending on the path you took to build out your site structure using the Minimal Mistakes theme (see [Part 2]({{ site.baseurl }}/personal website/PWHT-2-gotgitjekyll/){: style="color: #2980b9"} in my Personal Website series), you may not have `_data/navigation.yml` and `_data/ui-text.yml` in your site folder structure (recall, the gem-based verison hides many of the theme's folders from immediate view). You can read more about this in the theme documentation [here](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/).

You will need  to edit `_data/navigation.yml` to customize the navigation links you want for your site. `(_data\ui-text.yml` contains UI labels and text that appear throughout the site. If you want to customize these then you will have to copy and edit this file as well, but I won't be discussing it here).

## Site links
If not already present, copy [`_data/navigation.yml`](https://github.com/mmistakes/minimal-mistakes/blob/master/_data/navigation.yml) to your site root folder.

For every link you want to display in the top menu of your site, you specify it under the `main` key in `_data/navigation.yml`, and it looks like this:

    # main links
    main:
      - title: "Quick-Start Guide"
    	url: https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/
      - title: "About"
        url: /about/
      - title: "Sample Posts"
        url: /year-archive/

Each **title-url** pair correpsonds to a link (or page):
- `title` is the name of the page
- `url` is the link to the corresponding file with the contents of the page

For example, to add a site link `About`, insert the following two lines in `navigation.yml`:

	- title: About
	  url: /about/


## Adding a site page
For each site link in `navigation.yml` create a markdown file (.md or .markdown) in the `_pages` directory (create this directory at the root level of your site if you dont already have it). 

So for the link `About`, you have to create `about.md` with the following frontmatter (content between the two `---`):

	---
    title: "About"
    layout: single
    permalink: /about/
    author_profile: true
    ---

	Hi! Welcome to my site. The content here is in markdown.

- `permalink:` must match `url` in `navigation.yml` and must have the leading and trailing `/`
- `layout:` depends on how you want to present the page. `single` works for most use cases; for other uses see theme documentation on [layouts](https://mmistakes.github.io/minimal-mistakes/docs/layouts/).

## Adding a site link for Blog (or Posts)
As you may have noticed from the sample `navigation.yml` above, `url` for posts is specified differently:

      - title: "Sample Posts"
        url: /year-archive/

You can have any value for `title` (say "Posts", Blogs", "Articles"). But `url` takes the specific value `/year-archive/`. You have to create the corresponding **year-archive.md** file in the `_pages` folder with the following frontmatter:

    ---
    title: "Posts by Year"
    permalink: /year-archive/
    layout: posts
    author_profile: true
    ---

- `title` can be anything you like
- `permalink:` must be `/year-archive/`
- `layout:` must be `posts`
- `author_profile:` can be `true` or `false`

Minimal Mistakes reads **year-archive.md** and knows to link to all the posts in the `_posts` folder (as long as they follow the naming convention discussed below). The posts are automatically listed chronologically and organized by year. If you want to use a different organization, read more about [archive layouts](https://mmistakes.github.io/minimal-mistakes/docs/layouts/#archive-layout).


## Adding posts
**year-archive.md** is simply the landing page for your blog. To show posts on this page, you have to create posts.

You must save posts in the `_posts` folder.

Posts must be named with the convention: `Year(YYYY)-Month(MM)-Day(DD)-filename.MARKUP`.
- YYYY: four-digit number
- MM: two-digit number
- DD: two-digit number
- MARKUP: .md or .markdown

Minimal Mistakes requires posts to be **markdown** files, in the **`_posts`** folder, named as **YEAR-MONTH-DAY-title.MARKUP** to correctly identify them.

Example post:

    ---
    title:  "How to create a post?"
    date:   2021-04-06T12:00:00-0500
    excerpt: "Simple guide for creating a sample post."
    ---

	My first post.

- `title:` appears as the header at the top of the page in the post
- `layout:` defaults to single from `config.yml` (specify `layout:` in the frontmatter of the post if you want something different)
- `date:` date of the post
- `excerpt:` brief description of the contents in the post (unique descriptions help with SEO and site search and listings)

**Read Next:** [Personal Website – Part 4: Theme customization]({{ site.baseurl }}/personal website/PWHT-4-customization/)



