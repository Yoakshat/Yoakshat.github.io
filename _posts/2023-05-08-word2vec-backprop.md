---
layout: distill
title: The Math Behind Word2Vec
description: My first time with gradient calculus after we just learned it in math class 
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

I think after a lot of thinking, I know the big trick to gradient calculus. At first, I started
thinking about each changing parameter and I was super scared of a big neural network, because
I am not doing backprop for billions of parameters. We have our fav torch.grad() for that. 

But the trick is you can compute the gradient for just one parameter, and then just apply 
that to the entire vector. Haven't at all tested out in code! Oh no! But I'm pretty sure you can just
plug in the formula for one parameter for the entire vector and it should work! 

Like here, after learning mathjax I can finally compete with the mathy blogs - I've always wanted to do these! 
Watch this! 

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

The complete word2vec calculus is on the way... 