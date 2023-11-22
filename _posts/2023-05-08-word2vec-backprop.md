---
layout: distill
title: A Demo of Word2Vec
description: Going Behind the Scenes
giscus_comments: true
date: 2023-05-09
tags: math machine-learning

authors:
  - name: Akshat Mundra
    affiliations:
      name: The Deep Learning Community

# Optionally, you can add a table of contents to your post.
# NOTES:
#   - make sure that TOC names match the actual section names
#     for hyperlinks within the post to work correctly.
#   - we may want to automate TOC generation in the future using
#     jekyll-toc plugin (https://github.com/toshimaru/jekyll-toc).

    # if a section has subsections, you can add them as follows:
    # subsections:
    #   - name: Example Child Subsection 1
    #   - name: Example Child Subsection 2

# Below is an example of injecting additional post-specific styles.
# If you use
---

When you think you know everything about gradient calculus after you learn it in Calc class, you realize
you know nothing. Especially when deriving a derivative for billions of parameters and programming
backpropogation. Libraries like Pytorch and Tensorflow do all the hard backpropogation work for us, 
so why should we care?! 

Here is a demo of MathJax showing how to update weights with vectors & gradients. 

$$ \begin{bmatrix} w_0 & w_1 & w_2 \end{bmatrix} 
    - lr * \begin{bmatrix} 
    \frac{\partial L}{\partial \hat{p_0}}  
    \cr
    \frac{\partial L}{\partial \hat{p_1}}
    \cr
    \frac{\partial L}{\partial \hat{p_2}}
    \end{bmatrix} * 
    \begin{bmatrix}
     \frac{\partial \hat{p_0}}{\partial w_0} & 
     \frac{\partial \hat{p_1}}{\partial w_1} & 
     \frac{\partial \hat{p_2}}{\partial w_2}  
    \end{bmatrix}
$$


Now back on topic! In the Natural Language Processing field, years ago, Word2Vec was huge. Now we 
ignore it, having all these fancier-techniques. But TODAY, wanting to go back 
to the basics AND show a behind-the-scenes, here is a demonstration of Word2Vec I created: 

<a href="https://www.kaggle.com/code/akshatmundra/word2vec-from-almost-scratch">A Kaggle Notebook with a Word2Vec Demo</a>