---
layout: default
---

![Banner](assets/biscuit.png)

# “Creative breakthroughs occur, when worlds collide”

*Thai-Nam Hoang, Valentin Peyron, Paul-Bogdan Jurcut, Quentin Esteban, Jan Kokla*

In 2004, American entrepreneur Frans Johansson published the book
*“The Medici Effect: Breakthrough Insights at the Intersection of
Ideas, Concepts, and Cultures”* [[1](https://www.goodreads.com/pt/book/show/20482413)]. Quoted:

> We have met teams and individuals who have searched for, and found, intersec- tions between disciplines, cultures,
> concepts, and domains. Once there, they had the opportunity to innovate as never before, creating the Medici Effect.

In other words, by merging ideas from a range of diverse backgrounds,
one can increase the likelihood of intellectual cross-pollination,
which might lead to innovation and success.

Our aim is to examine if this holds true in the movie industry.
We focus on the plots and genres and with the help of the embedding
models we will generate the network graphs. These will help us to
verify if the relationship between “being at the intersection”
and the success are linked in the movie industry.

## Analysis

### 2.1. Distributions

{% include analysis/release_year_kde.html %}

Considering the distribution of the histogram, we might shift out focus for the last 40 years since there's more
available data.

{% include analysis/scatter_jointplot.html %}

As we can see, ratings are almost normally distributed. Additionally, higher spread in ratings also comes from the
recent decades.

### 2.2. Genre analysis

As our work will highly depend on the genres, let's take a look which are the most common and/or most rated.

{% include genre_ana/no_movie_genres.html %}

It turns out the most of the movies have 1-5 genres, but there might be as many as 17.

{% include genre_ana/no_movie_genres_bar.html %}

{% include genre_ana/rating_by_genre.html %}

As can be seen from the chart, there are no clear patterns regarding the rating and the genre, which is as expected.