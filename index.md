---
layout: default
---

![Banner](assets/banner.jpg)

# Creative breakthroughs occur, when worlds collide

*Thai-Nam Hoang, Valentin Peyron, Paul-Bogdan Jurcut, Quentin Esteban, Jan Kokla*

In 2004, American entrepreneur Frans Johansson published the book
*“The Medici Effect: Breakthrough Insights at the Intersection of
Ideas, Concepts, and Cultures”* [[1](https://www.goodreads.com/pt/book/show/20482413)]. 
In other words, by merging ideas from a range of diverse backgrounds,
one can increase the likelihood of intellectual cross-pollination,
which might lead to innovation and success. Our goal is to see if this 
holds true in the movie industry.

## "At the intersection"?

Before we can dive deep into the movies, let’s first think about the 
concept of “being at the intersection” for a second. Most natural way 
of looking at it is network graphs. With 2 simple examples, we will 
introduce the two measures that we’re going to use 
for quantifying it: **_degree_** and **_betweenness_**.

### Betweenness

If you take a look at the graph below, you see that we have 2 bigger 
clusters and one node that sits at the intersection. 
This is exactly what the Medici effect referred to! Visually it all looks 
really simple to grasp right, but how can we quantify it? This is where 
**betweenness** measure comes in.

{% include theory/betweenness.html %}

If you take all pairs of nodes from the graph and find the shortest paths 
between them, then betweenness centrality for a certain node is _the percentage 
of these shortest paths that go through the node_. If you now once again look 
at the graph above and focus on the colors of the nodes (you 
can hover over the nodes to see the numerical betweenness measure), you see 
that the lighter the color, the bigger the betweenness. We have 
successfully quantified “being at the intersection” for clustered network graphs.

### Degree

What if we don’t have such clear clusters, but we rather have a big chunk of quite 
similar movies and then some outliers as seen from the graph below? We don’t really 
have nodes that act as bridges between clusters and sit at the intersections. In 
that case, let’s redefine the Medici effect in the movie industry a bit and say 
that the most successful movies will be **the ones that have taken ideas from many 
other movies and thus are connected to the biggest possible number of other nodes**. 
You might already have guessed… degree of the node is exactly what we need.

{% include theory/degree.html %}

This time, the color of the node reflects the value of the degree (lighter color 
means higher degree). If you hover over the nodes, you can compare the betweenness 
and degree measures for the node. Naturally, the ones in the big cluster have higher 
degree, compared to the ones in the outskirts.

## What about the movies?

We have found ways for quantifying the centrality of the node, but how about movies? 
How can we generate a graph based on the data at hand? For that we came up with two 
alternative approaches, which include **embeddings** and **classification**.

### Embeddings

The idea is simple: find the similarity between all possible combinations of movies 
and if they're similar enough, create an edge. The reality is a bit more complex.
We first need to turn movies into vector representations. In order to do that , 
we'll use an embedding model 
[E5-large-v2](https://huggingface.co/intfloat/e5-large-v2) that takes the plot of 
the movie as an input and converts it into normalized vector with embedding size 
of 1024.

Once we have vectorized the plots, we can calculate the similarities between 
the plots with dot product because they are normalized to unit vectors. Below 
you can see an example of similarity matrix with 20 random movies. Notice that 
one of the quirks of the embedding model is that all the cosine similarities are
between 0.7 and 1.0. As we still have a distribution, it will not be a problem for
us.

{% include theory/similarity_matrix.html %}

Let's make a sanity check and take a look at the similarity matrix to see 
if it intuitively makes sense.
[Thelma](https://www.imdb.com/title/tt6304046/) and 
[Elektra Luxx](https://www.imdb.com/title/tt1340773/) tend to be quite similar to 
each other, and it seems so from the descriptions... female main characters 
struggling with their challenges. We can find 
[Gerald](https://www.imdb.com/title/tt1213900/) and 
[Kill Speed](https://www.imdb.com/title/tt1027683/?ref_=nv_sr_srsg_0_tt_8_nm_0_q_kill%2520speed) from the opposite
end with quite low similarity value. Gerald is a comedy of disabled guy and 
Kill Speed an action thriller about transporting drugs with planes.
