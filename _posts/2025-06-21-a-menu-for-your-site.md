---
title: A menu for your site
description: Configure a small top menu while keeping Biscuit's single-column layout.
tags: [Jekyll, Customization]
excerpt_separator: <!--more-->
---

A personal website can start with one page and grow into a few pages and a blog. Biscuit's top menu keeps those pages within reach, using a short list of links in the site configuration.

<!--more-->

## Set the links

Edit `navigation` in `_config.yml`:

```yaml
navigation:
  - title: Home
    url: /
  - title: Blog
    url: /blog/
  - title: About
    url: /about.html
  - title: Projects
    url: https://github.com/yourname
```

Internal paths start at the site root. Do not add your repository name to each link: Biscuit adds `baseurl` for you. External links keep their full address.

For a section on the home page, use a fragment such as `url: /#projects`. The shorter `url: "#projects"` also returns to that section from a blog post; quote it because `#` starts a comment in YAML.

## Keep navigation simple

The current page is highlighted automatically. Blog posts keep the Blog link highlighted. If you create another group of pages, set `nav_section` in their front matter to the corresponding menu URL.

On narrow screens, links wrap onto another row. The bar scrolls with the page on small or short screens, leaving room for reading.

## Use a single page

To hide the menu, remove the navigation list or replace it with:

```yaml
navigation: []
```

The page then uses Biscuit's original top spacing. To hide the recent posts on the home page, remove `show_recent_posts: true` from `index.md`.

You can use a menu without a blog, a blog without a menu, or both together.
