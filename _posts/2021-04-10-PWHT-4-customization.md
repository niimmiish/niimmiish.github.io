---
title:  "Personal Website – Part 4: Theme customization"
date:   2021-04-10T12:30:00-0500
show_date: true
toc: true
categories:
  - personal website
tags:
  - jekyll
  - github
  - posts
  - minimal mistakes
excerpt: "How to customize some aspects of the Minimal Mistakes theme."
---

> <span style="color: #596275">Few tips for Minimal Mistakes theme customization.</span>

This website is built with Jekyll and the Minimal Mistakes theme, and I host it on GitHub Pages. I author content in Markdown and incrementally build and test the site locally. Once I am satisfied, I push the changes to my GitHub repository, where the site is rebuilt and the changes are live.

I tweaked the Minimal Mistakes theme a little bit to suit my liking. Given I don't have a web development background, it took me a lot of fumbling and reading and experimenting to figure out where to make edits. Read on for a few tips if you are looking to customize some aspects of the theme — it may save you time.

## Helpful theme documentation
The documentation for Minimal Mistakes is excellent. In fact, it takes a while to go through all of it and it's a bit intimidating if you don't know a little something about web development. While figuring out customizations I wanted to make, I found myself going through these links a whole lot:

- [Overriding theme defaults](https://mmistakes.github.io/minimal-mistakes/docs/overriding-theme-defaults/)
- [Sidebar](https://mmistakes.github.io/minimal-mistakes/docs/layouts/#custom-sidebar-navigation-menu) and [custom sidebar navigation](https://mmistakes.github.io/minimal-mistakes/layout-sidebar-nav-list/)
- [Splash page layout](https://mmistakes.github.io/minimal-mistakes/docs/layouts/#splash-page-layout)
- [Header overlay](https://mmistakes.github.io/minimal-mistakes/docs/layouts/#header-overlay)
- [Using images](https://mmistakes.github.io/minimal-mistakes/post%20formats/post-image-standard/)
- [Image Alignment](https://mmistakes.github.io/minimal-mistakes/markup/markup-image-alignment/)


## Author bio size and style
- What to edit: `_sidebar.scss`
- Find: `.author__bio`
- Add / change: `font-size` and `font-style`

```
.author__bio {
  margin: 0;
  font-size: 1.0em;
  font-style: italic;

  @include breakpoint($large) {
    margin-top: 10px;
    margin-bottom: 20px;
  }
```
Other author related customizations can be made here as well.


## Font sizes
To change font size everywhere.
- What to edit: `_reset.scss`
- Find: `html{ }`
- Change: `@include breakpoint` values. In my case, I have the following:

```
 @include breakpoint($medium) {
    font-size: 15px;
  }

  @include breakpoint($large) {
    font-size: 16px;
  }

  @include breakpoint($x-large) {
    font-size: 17px;
```

## Primary color, link color
- What to edit: Your skin's `.scss`. In my case, `_contrast.scss`
- Change: `$primary-color` and `$link-color` values. I used:

```
$primary-color: #0a3d62 !default;
$link-color: #686de0 !default;
```
**Note**: You can change a host of default skin settings in your chosen skin's .scss file.
{: .notice--info}


## TOC positioning and float
For a floating TOC on the right.

- What to edit: `_sidebar.scss`
- Find: `.sidebar__right`
- Comment out: `position: absolute;`
- Add:
```
position: sticky !important;
float: right !important;
padding-top: 1em !important;
```

## Navigation links color, TOC title fill color, TOC active item
- What to edit: `_navigation.scss`

**For navigation links color:**
- Find: `.visible-links`, `a { &:before{ }}` in *Priority plus navigation* section, 
- Add:
```
background-color: #0a3d62;
```

**For TOC title fill color:**
- Find: `.nav__title` in *Table of contents navigation* section
- Add:
```
background-color: #4b6584;
```

**For marking active item in TOC when scrolling:**
- Find: *Table of contents navigation* section
- Comment out: `@include yiq-contrasted($active-color);`
- Add:
```
@include yiq-contrasted(mix(#fff, #a4b0be, 80%)); 
```
