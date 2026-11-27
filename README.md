# Biscuit theme for Jekyll

[Biscuit](https://sblisesivdin.github.io/biscuit/) is a simple, responsive Jekyll theme for personal websites and blogs. Use one page, add a top menu, or publish Markdown posts with the same clean layout.

## Getting started

Fork this repository and enable GitHub Pages from your `gh-pages` branch. Edit `_config.yml` and replace the example content in `index.md` and `_posts/`.

Set the site address in `_config.yml`:

```yaml
title: Your name
description: A short description of your website.
url: "https://yourname.github.io"
baseurl: "/your-repository"
```

For a user site named `yourname.github.io`, or a custom domain served at its root, use `baseurl: ""`. This repository's demo uses `/biscuit`. Internal menu and asset paths should **not** include `baseurl`; the templates add it.

For local use, install [Ruby and Jekyll's prerequisites](https://jekyllrb.com/docs/installation/), then run:

```sh
bundle install
bundle exec jekyll serve
```

The Gemfile uses `github-pages` to match GitHub Pages' supported Jekyll and plugins. With the demo settings, open `http://localhost:4000/biscuit/`. Restart Jekyll after changing `_config.yml`.

## Top menu

Set the links and their order in `_config.yml`:

```yaml
navigation:
  - title: Home
    url: /
  - title: Blog
    url: /blog/
  - title: About
    url: /about.html
  - title: Projects
    url: /#projects
  - title: GitHub
    url: https://github.com/yourname
```

An internal URL begins with `/`. Full external URLs and `mailto:` links are also supported. For a home-page section, use `/#projects` or `"#projects"`; quote a leading `#` in YAML. Section links lead to the home page even when followed from a post.

The current page is highlighted, and posts keep the Blog link selected. To group other pages under a menu item, set `nav_section: /about.html` in those pages' front matter, matching the menu URL. Fragment links are not automatically highlighted while scrolling.

The menu wraps on small screens and remains usable without JavaScript. It stays at the top while scrolling on larger screens. Its styles are scoped to the menu.

For the original layout without a menu, remove the list or set `navigation: []`. No menu space is reserved when the list is empty.

## Blog

Create `_posts/YYYY-MM-DD-title.md`:

```markdown
---
title: My first post
description: A short description for search results and link previews.
tags: [Research, Python]
---

The first paragraph becomes the summary in the blog list.

## A section

The rest of the article goes here.
```

The post layout is assigned automatically. The archive at `/blog/` lists posts newest first. Posts use `/blog/title/` URLs, independent of their tags. Each article includes its date, optional tags and author, adjacent post links, and a link back to the archive. Tags are displayed as labels, not separate archive links.

Optional front matter:

```yaml
author: Your name
last_modified_at: 2026-11-27
excerpt_separator: <!--more-->
```

Use `last_modified_at` when updating a published article. With `excerpt_separator`, place `<!--more-->` after the introduction. Without it, Jekyll uses the first paragraph.

Store figures and downloads under `assets/`. In Markdown, use Liquid for site-relative URLs:

```liquid
![Figure description]({{ '/assets/my-figure.png' | relative_url }})
[Download data]({{ '/assets/results.csv' | relative_url }})
```

Code blocks and wide article tables scroll horizontally. Images fit the content column. There is no required cover image or client-side script.

### Recent posts on the home page

Add `show_recent_posts: true` to the front matter of `index.md`. Configure the number of posts and date format in `_config.yml`:

```yaml
blog:
  recent_posts: 3
  date_format: "%b %-d, %Y"
```

Remove the page setting to hide the list, or set `recent_posts: 0`. Nothing is displayed if there are no published posts.

### Drafts

Keep unfinished posts in `_drafts/title.md` without a date in the filename. Preview them with:

```sh
bundle exec jekyll serve --drafts
```

A normal build omits drafts and future-dated posts. Drafts in a public repository are still readable as source on GitHub; use a private working copy for confidential material.

### Feed and sharing

`jekyll-feed` generates `/feed.xml`, linked from the archive and the document head. `jekyll-seo-tag` generates page titles, canonical links, and sharing metadata. Both plugins are supported by GitHub Pages. Set `url`, `baseurl`, and each post's title and description accurately. An optional `image` in a post's front matter supplies a social preview image.

### A site without a blog

Remove the Blog menu item, the `show_recent_posts` setting, `blog/index.html`, and the example files in `_posts/`. If you also remove `jekyll-feed` from `plugins`, remove `{% feed_meta %}` from `_layouts/default.html`. The menu and ordinary pages work independently of the blog.

## Files

| File | Purpose |
| --- | --- |
| `_config.yml` | Site settings, menu, and blog defaults |
| `index.md` | Home page |
| `_posts/` | Published Markdown articles; replace the examples |
| `blog/index.html` | Blog archive and feed link |
| `_layouts/default.html` | Shared HTML document |
| `_layouts/post.html` | Article layout |
| `_includes/navigation.html` | Configurable top menu |
| `_includes/post-list.html` | Shared list of post summaries |
| `_includes/recent-posts.html` | Optional recent posts section |
| `_includes/head.html` | Custom additions to the document head |
| `_includes/scripts.html` | Footer and custom additions before `</body>` |
| `_sass/` | Theme, menu, blog, and syntax styles |
| `css/main.scss` | Stylesheet entry point |

## License

Biscuit is derived from the deprecated [Solo](https://github.com/chibicode/solo) theme and maintained by [Sefer Bora Lisesivdin](https://sblisesivdin.github.io/).

Biscuit and the original Solo code are distributed under the [MIT license](LICENSE).
