---
title: Writing with Biscuit
description: Publish a Markdown post with code, images, and a short introduction.
tags: [Jekyll, Markdown]
excerpt_separator: <!--more-->
---

A blog post is a Markdown file with a title and a date. Biscuit supplies the layout, a place in the archive, and links to the other posts. This example shows the pieces you can use in your own writing.

<!--more-->

## Create a post

Add a file such as `_posts/2025-06-20-my-first-post.md`. Start it with a short settings block:

```yaml
---
title: My first post
description: A short description for search results and link previews.
tags: [Research, Python]
---
```

Write the article below that block. The date in the filename determines its publication date. The layout is assigned automatically by `_config.yml`.

## Include code and results

Fenced code blocks keep commands and programs readable:

```python
energies_ev = [-10.42, -10.57, -10.53]
minimum_ev = min(energies_ev)
print(f"Minimum energy: {minimum_ev:.2f} eV")
```

| Quantity | Value |
| --- | ---: |
| Minimum energy | −10.57 eV |
| Number of samples | 3 |

These values are an illustration of formatting, not a materials calculation.

## Add an image

Use `relative_url` for site assets so that the same post works on a user site and in a project subdirectory:

{% raw %}
```liquid
![A description of the figure]({{ '/assets/my-figure.png' | relative_url }})
```
{% endraw %}

Images are optional. A post can be a few paragraphs, a short tutorial, or a longer article with figures and tables.

## Choose the summary

By default, the first paragraph appears in the blog list. To use a longer introduction, add `excerpt_separator: <!--more-->` to the settings block and put `<!--more-->` where the introduction ends.

For unfinished work, keep the file in `_drafts/` without a date in its filename and preview it locally with `bundle exec jekyll serve --drafts`. Draft files are not included in a normal build. In a public repository, their source files are still public.
