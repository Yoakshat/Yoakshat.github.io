---
layout: distill
title: Health + AI Research
description: Currently what I am working on...
giscus_comments: false
date: 2023-7-29
tags: math machine-learning

authors:
  - name: Akshat Mundra
    affiliations:
      name: North Creek HS
---

*I want to credit my mentor Gabriel Barner Erion for giving me some of these ideas and discussions which led to the spark of my own ideas*

## Introduction

Hospitals can benefit from Artificial Intelligence with tasks like predicting if a patient is going to be readmitted or not. For example, if a model outputs yes to be readmitted, hospitals may choose to schedule a primary care visit within a week. This helps both care outcomes and makes sure the hospital is running efficiently. No longer, will that readmitted patient take extra space in the intensive care unit (ICU)!

Using discharge summaries, many machine learning models have been 
trained on this task. Discharge summaries are what a doctor writes just before the patient is discharged, with information 
about the entire patient's stay. However, often these summaries are templated. Now imagine every time an ice-cream truck comes to the beach, 
the tides grow bigger. It's a coincidence but if that's the only thing you saw, the next time you saw an ice-cream truck you'd say the tides are going
to grow bigger. To remove this type of correspondence, this research asks what happens if we remove templates from discharge summaries? 

## Finding Templates 

Imagine you had a function to determine the similarity between two documents: $$sim(doc1, doc2)$$. 
The documents that are the closest together in a representation space, will often be templates. 

## Transforming Text into a Representation Space

Machines, computers, and math all understand numbers not words. One way to encode a document is with 
**bag-of-words**, which creates a vector of word frequencies. Imagine you have a dictionary 
like [loves, he, mom]. 

Your sentence "he loves loves mom" will be transformed into the vector [2, 1, 1]. Let's show how this can be done in code!

```py
from sklearn.feature_extraction.text import CountVectorizer
def transform(texts){
    return CountVectorizer().fit_transform(texts)
}
```

Then, we might define the similarity function of two vectors as: 

```py
import numpy as np
def similarity(vector1, vector2){
    return np.sum((vector2 - vector1)**2); 
}
```

This is just the euclidean distance between both vectors, but without the square root! Using this code, you can compare one document 
to thousands of other documents. Then, the top ten are likely templates. However, an even better way of finding templates doesn't require
**bag-of-words**. For finding templates, **one-hot-encoding** actually seems to be better. 

**One-hot-encoding** means that if the dictionary is [loves, he, mom] and the sentence is "he loves loves mom", this sentence will be 
transformed into the vector [1, 1, 1]. A word is only counted once. In other words, we only care if a word is present or not present! 

## Algorithm 1

1. Turn documents into vectors with one-hot-encoding
2. Loop through vectors and compute similarities with all others 
3. If there are over 50 documents that are **highly similar** (greater than some threshold), put these documents into one template 

```py
def find_templates(texts): 
    templates = []
    # turns documents into vectors with one-hot-encoding
    vectors = one_hot_encode(texts)

    for v in vectors: 
        # compute similarity with all vectors
        simScores = similarityAll(v, vectors)
        # if over 50 documents
        if np.sum(simScores >= 0.9) >= 50: 
            # place these documents into one template
            templates.append(texts[np.where(simScores >= 0.9)[0]])
```

We actually use a different similarity function than euclidean distance, which proves better at finding templates! Here's the psuedocode! 

```py
def similarity(vector1, vector2): 
    '''
    Take the number of words in document one that document 2 shares and divide it by the unique words of document 1
    Do the vice-versa
    Then average them to get a score
    '''
```

## Algorithm 2 

1. Turn documents into vectors with one-hot-encoding
2. Perform hierarchal clustering onto vectors, which automatically generates templates by merging the most similar vectors at every iteration!
3. Create an interactive that lets you visualize templates (I used Dash!) to figure out when you've found all the templates

There's a really nice video on hierarchal clustering that's the best to explain: <a href="https://www.youtube.com/watch?v=7xHsRkOdVwo">StatQuest Video</a>

A brief overview of hierarchal clustering is every iteration, it merges the closest groups together! At the end, all the documents will be in one group (it's like a genetic tree from all the species to Adam and Eve). I make the assumption that because 
**templates will always be the most similar to each other** we can end at the iteration where the next vector or group merged which isn't a template

Watch the StatQuest video, seriously! 

## Algorithm 3 

This algo is very similar to the last one! Hierarchal clustering starts by merging individual vectors and then starts merging groups. Now how do you 
compute the similarity between two groups. You compute the centroid of both groups and then find the similarity between them. 

Instead of centroid, in this algorithm we use the mode of the groups. This means if our group was

[1, 1, 0]
[1, 1, 0]
[1, 1, 1]

The mode would be [1, 1, 0]. The reason for using mode is it likely does a better job at recognizing templates. 
Modes are particularly better because [1, 1, 0] represents all the parts that are templated (all the common words). 
Since we are looking for documents that have these common words, we would want to compare it to just these common words! 

Also algo 2 used the similarity function of euclidean distance (mainly because it was convenient to plug in scipy's version of hierarchal clustering 
without having to do much work)! 
Algo 3 uses the same similarity function as algo 1! 

## Results 
A logistic regression model is as good as an XGBoost, or a KNN, to predict readmission. In this case, 
we feed the model **bag-of-words**. How does removing templates via all three algorithms, affect the logistic regression model's performance? 

We actually test two things. 
1. What happens if we remove the templated words inside the document (zero them out in our vector)?
2. What happens if we half their word-count (deem them as not as important)? 

**Algorithm 1**

V1: removing them completely
<div class="row mt-3">
   <div class="col-sm mt-3 mt-md-0">
       {% include figure.html path="assets/img/modesfast0.png" class="img-fluid rounded z-depth-1" zoomable=true %}
   </div>
</div>

**IMPORTANT**

On the x-axis is the ratio of templates:all other documents. The reason for this measurement is most likely, if 
there are a great number of templates relative to other documents, it will hinder the model's performance. Otherwise, it won't 
hinder it as much. 

On the y-axis is AUROC (Area Under The Receiver Operating Characteristic). The best way to explain is it's the area under this curve! You can notice why 1 is the best score!
<div class="row mt-3">
   <div class="col-sm mt-3 mt-md-0">
       {% include figure.html path="assets/img/roc-curve-v2.png" class="img-fluid rounded z-depth-1" zoomable=true %}
   </div>
</div>

The green line represents the versions without templates. The red line represents the versions with templates. 
The dashed lines represent the validation set, the data the model hasn't seen, while solid lines represent the training set. 

What you should be looking for is are the green lines generally at least 5% higher than the red lines? 


V2: 50% removal
<div class="row mt-3">
   <div class="col-sm mt-3 mt-md-0">
       {% include figure.html path="assets/img/modesfast0.5.png" class="img-fluid rounded z-depth-1" zoomable=true %}
   </div>
</div>

**Algorithm 2**

V1: removing them completely
<div class="row mt-3">
   <div class="col-sm mt-3 mt-md-0">
       {% include figure.html path="assets/img/dendogram0.png" class="img-fluid rounded z-depth-1" zoomable=true %}
   </div>
</div>

V2: 50% removal 
<div class="row mt-3">
   <div class="col-sm mt-3 mt-md-0">
       {% include figure.html path="assets/img/dendogram0.5.png" class="img-fluid rounded z-depth-1" zoomable=true %}
   </div>
</div>

**Algorithm 3**

V1: removing them completely
<div class="row mt-3">
   <div class="col-sm mt-3 mt-md-0">
       {% include figure.html path="assets/img/custom0png.png" class="img-fluid rounded z-depth-1" zoomable=true %}
   </div>
</div>

V2: 50% removal
<div class="row mt-3">
   <div class="col-sm mt-3 mt-md-0">
       {% include figure.html path="assets/img/custom0.5.png" class="img-fluid rounded z-depth-1" zoomable=true %}
   </div>
</div>

## The Conclusion
We seem to have disproved our hypothesis: templates don't affect machine learning models, even simple like Logistic Regression! 
Well not really, there are still so many new ideas we want to try! 

1. When we actually remove the templated words, we are removing all signs of such word, not just the templated part! Here is an example, 
"I want to bat a tennis ball with a bat" 
"I want to bat a soccer ball with a cat"

The template is "I want to bat a _ ball with a _." We suboptimally, remove all these words. Now when we remove the word, "bat," in the first sentence shown, 
it also removes the last word of the first sentence (not actually part of the template)!

We still have to figure out how to fix that! 

2. What if we're not recognizing all the templates? We really want to try **multi-sequence alignment programs**. 
Usually, these programs are used on DNA segments to identify common strands. This is used, for example, to notice 
how similar DNA segments are and build real genetic trees! 

Now, we want to use this on text! Can it find templates like it finds common strands in DNA?!

**We're not done yet!**
















