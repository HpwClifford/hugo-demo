+++
title = "Hugo Setup"
date = 2022-06-14T23:03:20-04:00
weight = 2
chapter = true
pre = "<b>II. </b>"
+++

### Hugo

# Setup Guide

## I.) basic setup

Using the hugo cli, we can generate a new project directory within our existing project:

```sh
hugo new site web
```

Then, we'll select a theme and add it as a github submodule. Here's how I downloaded the theme for this site:

```sh
git submodule add https://github.com/matcornic/hugo-theme-learn web/themes/hugo-theme-learn
```

And that's it! We have the basic setup to build a hugo site. Let's get building!

Note: from here on out, all commands should be executed from the **_web/_** directory.

## II.) creating site content

We can use the hugo cli to start a local development server:

```sh
hugo server
```

This will provide a fast-reloading dev environment and will default to serve our site at **https://localhost:1313/our-repo/**

```sh
Start building sites … 
hugo v0.100.2+extended darwin/amd64 BuildDate=unknown

                   | EN  
-------------------+-----
  Pages            | 12  
  Paginator pages  |  0  
  Non-page files   |  0  
  Static files     | 75  
  Processed images |  0  
  Aliases          |  0  
  Sitemaps         |  1  
  Cleaned          |  0  

Built in 44 ms
Watching for changes in /Users/harry.clifford.getweave/Development/go/src/hugo-demo/web/{archetypes,content,data,layouts,static,themes}
Watching for config changes in /Users/harry.clifford.getweave/Development/go/src/hugo-demo/web/config.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/hugo-demo/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```

From here we can use hugo and our configured theme to build the site. Links to docs:

[Hugo Docs](https://gohugo.io/documentation/)

[Learn Theme Docs](https://learn.netlify.app/en/)