---
layout: distill
title: Unsupervised learning is weird!
description: just talking about machine learning
giscus_comments: true
date: 2023-4-12


authors:
 - name: Akshat Mundra
---


Unsupervised learning is a very weird world. Imagine you are walking
down a park, sit on a bench, and then get some wise words from an older person.
The words don't make any sense, but somehow they give structure to your life. I am
not sure many of you have had that experience, but unsupervised learning uses nothing
(except some scientist's statistical techniques) to find structure in the data.




Monty Python (oops I mean Monty Hall) is also a weird problem but statistics tell us the answer.
In this post, I'm going to pull infamous examples of unsupervised learning that have blown scientists
away!


<div class="row mt-3">
   <div class="col-sm mt-3 mt-md-0">
       {% include figure.html path="assets/img/montyhall.png" class="img-fluid rounded z-depth-1" zoomable=true %}
   </div>
</div>


<h1>tSNE embeddings with Brawl Stars</h1>


One interesting unsupervised technique is <a href="https://www.jmlr.org/papers/volume9/vandermaaten08a/vandermaaten08a.pdf">tSNE embeddings</a>. The S stands for stochastic, which means an 'estimation.' The classic example is a ball rolling down a hill, but you have no idea where the ball is going to end up. Now comes an example related to what we love, playing Brawl Stars! As a brawler, you're noticing hmmm let's draw a boundary here. After all, we can't have Crow
and Leon attacking each other right in the start! Now let's continue drawing boundaries, until we have a pretty fair map!




For the non Brawl-Star readers, first of all, I'm sorry. Hopefully you've heard of the game Catan. Everyone knows
the process of changing the hexagons so no stones are nearby, no 3 adjacent hexagons are too powerful. That is a
'stochastic' description of how tSNE works, but instead of setting the Catan board up or creating a Brawl Stars map,
it's taking high-dimensional data and transforming it into low-dimensional data. The idea is that data points nearby
in high dimensions should also be nearby in the transformed dimensions (e.g. Leon and Leon should be close together,
but not Leon and Crow).


A really nice explanation with visualizations is <a href="https://www.enjoyalgorithms.com/blog/tsne-algorithm-in-ml">here</a>.


<div class="row mt-3">
   <div class="col-sm mt-3 mt-md-0">
       {% include figure.html path="assets/img/brawl.png" class="img-fluid rounded z-depth-1" zoomable=true %}
   </div>
</div>


<h5>What has tSNE been used for?</h5>
Imagine <a href="https://www.nature.com/articles/s41467-019-13056-x">RNA expression levels for thousands of genes from up to millions of cells"</a>. How do you compare single cells with millions of information? Think about why tSNE is there, because 'life' is very complicated (get it haha). And maybe if you find a single cell that on a 2D graph
is near another one that scientists know, you can tell that cell's purpose. Maybe inside the cell, a gene is being
regulated that is causing a disease.




Or maybe <a href="https://www.kaggle.com/code/vatsalmavani/music-recommendation-system-using-spotify-dataset">Spotify</a> wants to take the audio features of the song, and based on the songs you like, tell you what other songs you'll like (e.g. sound similar). Or even maybe Spotify wants to give you vastly different song recs so you can explore your music
taste!


<h2>Zero shot learning</h2>
I don't know if zero shot learning is an example of unsupervised learning, but the idea is that it
can learn new concepts without have any data. So for example when you were a baby, you saw penguins, koalas,
snakes, pandas, but you never saw a Giraffe. You didn't even know it was called a Giraffe! So you decided to
call it tall white animal with golden spots.




You don't need any labels (kind of the idea of unsupervised learning). This paper in 2015 that I have absolutely
not read, but <a href="https://proceedings.mlr.press/v37/romera-paredes15.html">caught my attention</a> because it
discusses how a one-line solution beat SOTA in zero-shot learning. It's definitely interesting, but that's all I want
to talk about it for now!


<div class="row mt-3">
   <div class="col-sm mt-3 mt-md-0">
       {% include figure.html path="assets/img/v7labs.png" class="img-fluid rounded z-depth-1" zoomable=true %}
   </div>
</div>


<h2>Let's talk about Autoencoders!</h2>
Have I ever heard anyone that excited about autoencoders?! Actually, yes. <a href = "http://ufldl.stanford.edu/tutorial/unsupervised/Autoencoders/">A nice read on autoencoders</a>.


Even autoencoders would probably be excited about themselves because they love to learn! Let me explain. The sort of
motivation goes like we love discovering things ourselves without anyone's help. Let's give you a neural network and
all you have to do is take your image and output that same image.




But we're going make life very hard for you! We're going to add an activation (so you can't just have weights with 1,
1, 1, 1), we're going to turn off some of your neurons. It's hell, but by trying to get out of that hell, the autoencoder learns hey, maybe, if I figure this is grass most of the pixels around are grass. And so on.


<div class="row mt-3">
   <div class="col-sm mt-3 mt-md-0">
       {% include figure.html path="assets/img/hell.jpeg" class="img-fluid rounded z-depth-1" zoomable=true %}
   </div>
</div>


Unsupervised learning is a very weird statistical world! Put in an input of the Multiverse, you might get an output
of the Rick and Morty-verse. It's a magical thing!








<i>Goodnight even though it's not night,
yall!</i>





