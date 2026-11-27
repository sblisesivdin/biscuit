---
layout: default
title: Home
show_recent_posts: true
---

![Biscuit]({{ '/assets/biscuit.png' | relative_url }})


**[Biscuit](https://sblisesivdin.github.io/biscuit)** is a simple, responsive Jekyll theme for personal websites and blogs. Keep a single page, add a top menu, or publish Markdown posts with the same clean layout.

## Usage

You can use this theme with [Jekyll](http://jekyllrb.com/) or simply use it with [GitHub Pages](https://pages.github.com).
For local usage, simply download [Jekyll](http://jekyllrb.com/) and follow the installation guide for more information. You can download the latest Biscuit from [its Github repository](https://github.com/sblisesivdin/biscuit).

If you prefer to use GitHub Pages, you do not need to download it, upload files to a new repository, etc., just [fork](https://docs.github.com/en/get-starter/quickstart/fork-a-repo) and use it.

### Files

* `_config.yml`            : Main configuration file.
* `index.md`               : Website page (for now, this page).
* `_includes/head.html`    : File to add custom code to `<head>` section.
* `_includes/scripts.html` : File to add custom code before `</body>`. You can change footer at here.
* `_includes/navigation.html` : Top menu, configured in `_config.yml`.
* `_layouts/post.html`     : Blog post layout.
* `_posts` folder          : Blog posts written in Markdown.
* `blog/index.html`        : Blog archive, newest posts first.
* `_sass` folder           : Related scss files can be found at this folder.
* `css/main.scss`          : Main scss file.
* `README.md`              : A simple readme file.

## Example tag usage

## Header 1
### Header 2
#### Header 3
**bold**
*italic*

> blockquotes

~~~python
import os,time
print ("Biscuit")
~~~

## Licence and Author Information

Biscuit is derived from the currently deprecated theme [Solo](http://github.com/chibicode/solo). The development of Biscuit is maintained by [Sefer Bora Lisesivdin](https://sblisesivdin.github.io).

Biscuit and the previous code, where Biscuit is derived, are distributed with [MIT license](https://github.com/sblisesivdin/biscuit/blob/gh-pages/LICENSE).
