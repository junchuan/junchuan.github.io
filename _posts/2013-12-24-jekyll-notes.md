---
title: Jekyll Notes
date: 2016-08-12 13:22:12
categories:
- notes
tags:
- jekyll

---

This post introduces the essential stuff you need to know to use `jekyll` as a blogging tool.  

## What's jekyll?
A tool that allows you to write and generate static websites. It provides some scaffolding resources that help you write static websites/blogs faster.   
## Why do I learn jekyll?
Github supports it. 
## _config.yml

Each site has one `_config.yml` file, which controls how the Jekyll engine generates and organizes different webpages.  
## front matter
Any file that contains a [`YAML`](https://en.wikipedia.org/wiki/YAML) front matter block will be processed by Jekyll engine as a special file.  The front matter must be the first thing in the file and must take the form of valid `YAML` set between triple-dashed lines.
```
---
layout: post
title: Blogging Like a Hacker
---
```
### global variables 
`layout`:  layout files must be placed in the  `_layouts` directory.   
`permalink`: if you need your processed blog post URLs to be something other than the site-wide style (default `/year/month/day/title.html`), then you can set this variable and it will be used as the final URL.  
`published` : set to false if you don’t want a specific post to show up when the site is generated.  
### custom variables
Any variables in the front matter can be referenced in the page. 
## write a post
With these essential elements, you can then use `Markdown` to write your posts, however, `HTML` is also supported. 

---
## Reference links  

[http://marklodato.github.io/visual-git-guide/index-en.html](http://marklodato.github.io/visual-git-guide/index-en.html)  



