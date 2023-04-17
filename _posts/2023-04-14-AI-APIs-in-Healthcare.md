---
layout: distill
title: AI APIs in Healthcare
description: how AI is being brought to medical experts with no AI expertise
giscus_comments: true
date: 2023-04-14

authors:
  - name: Akshat Mundra
    affiliations:
      name: North Creek HS

# Optionally, you can add a table of contents to your post.
# NOTES:
#   - make sure that TOC names match the actual section names
#     for hyperlinks within the post to work correctly.
#   - we may want to automate TOC generation in the future using
#     jekyll-toc plugin (https://github.com/toshimaru/jekyll-toc).
toc:
  - name: Introduction
  - name: Technology APIs
  - name: AI No-Code Software
  - name: Conclusion 
    # if a section has subsections, you can add them as follows:
    # subsections:
    #   - name: Example Child Subsection 1
    #   - name: Example Child Subsection 2

# Below is an example of injecting additional post-specific styles.
# If you use this post as a template, delete this _styles block.
---

## Introduction
People are thinking that the new best people in any field will be the people 
who know how to use AI the 'best way.' They know how AI can best combine with their creative
mind and efforts. They may be right or absolutely wrong. 

AI developers are working to democratize AI, to bring a no-code workspace but still modify the 
AI to more of their liking. To take their expert knowledge and augment the AI with it. Then maybe 
when we get this, physicians and doctors won't be frustrated that neural networks are 'black boxes.' 
Instead they can be like a puppet steering the AI in the right direction and checking if the math 
behind the scenes is leading to the right results. 

So as of today, what are the AI APIs in healthcare that do this sort of thing? 

## Technology APIs
In the healthcare world, technology API companies are growing and becoming unicorn companies. Optum,
under the same creators of UnitedHealth, is one of the biggest data analytics arms for healthcare 
companies to directly plug in. Healthcare is very complicated, so if a tool doesn't provide any 
overhead stress but makes life easier, it's a good pitch. 

There are also APIs like Particle Health. As an introduction, healthcare requires great security, 
anonymization, so if we wanted to have an API where hospitals could access patient records just from
their name we wouldn't be able to. It'd be extremely helpful to hospitals, but also lead to needing
cybersecurity teams constantly battling the hacking going on (while billions of records are at risk). 
What Particle Health does is instead use patient demographics to find a patient and all of their 
records; it's a great and simple idea!

Brendan Keeler in his new quirky post on April 10 called "Super Integration Fighter III" splits software into the "atomic units," databases, user interfaces, and system interfaces. 

Healthcare tends to outsource a lot of things to APIs (especially now with physician burnout on a high where it's better for tech to do some of the jobs). Keeler talks about how when we get to the optimal stage, of any hospital or clinic being able to access a patient's data or use an API that connects all patients, we'll have to throw away the idea of tech siloes. It'll be hard but either there'll need to be a common data format (like FHIR which makes it easy) or even what would be interesting, a way hospitals could easily change the API for their use case with low-code. 

I really want to talk about this part, about getting the power of APIs in the hospital's hands and obviously with AI, because that's been my craze for a long time and now on everybody else's trending page. 

## AI No-Code Software 
After searching around, there is not much research on AI low-code or no-code software IN HEALTHCARE. We've heard 
of AI being used for finding similar gene expressions, for making DNA/RNA sequencing cheap, but what about deployment? 
AI will accelerate, but now hasn't really, but let's look at how AI low-code software will work practically? 

Brainstorming a few applications off my mind 
- If a doctor doesn't agree with the AI model say taking an image and predicting cancer, the doctor can type into the AI their
reasons and the AI might augment its prediction (we're not there yet). 
- More API-style, you tell your AI your use case and they look through the EHR to find what information you need (this could be really cool)
- AI APIs don't just need to be doctor facing but can also be patient-facing helping them distill hard-to-understand medical information 

With all the processing tasks, my imagination of low-code is there are differences across each clinic? Can you find some way to embed information in the AI that tells them because of this difference, do this task this way. Because there are common use cases, but a billion different data formats, a billion different little things to do. If we get every sort of data to be machine-readable, throw away the idea of a common data format (like FHIR), we'll let the AI do its work! 

## Conclusion 
I think what this is getting at is what we call multi-task learning in AI. An AI tried out a bunch of different data problems. Now the AI knows I can use how I solved all these other problems, to solve this new problem, even though it looks 
different! And this is how academics learn, how people learn. Researches have tried different neural networks, RNN, ANNs, Transformers, hundreds of times, and they have some intuition on what model they should use for a new problem. 

Instead of the billions of different AI applications we're seeing (like AI art-generation, AI text-generation, AI Q&A) I think we achieve real human-computer interaction when you can talk to it in some sort of semi machine-human language (not code) and it can do whatever you want. 

Then again, I wouldn't think it would be frustrating if it was like a vending machine or a drink machine, where you click what application you want (text generation, art generation, Q&A). That'll only be $1.50 (vending machine joke). Then the machine figures how to do the task for your set of data. It's all interesting, futuristic, and awesome!


<i>Goodnight even though it's not night,
yall!</i>
