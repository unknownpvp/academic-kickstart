
---
title: Phase 2 - Classifier
summary: Here we describe how to add a page to your site.
date: "2018-06-28T00:00:00Z"

reading_time: false  # Show estimated reading time?
share: false  # Show social sharing links?
profile: false  # Show author profile?
comments: false  # Show comments?

# Optional header image (relative to `static/img/` folder).
header:
  caption: ""
  image: ""
---

GameLab's classifier will allow user to input text to generate genre. 

The text classification identifys and defines the text based on class. I implemented Naive Bayes algorithmn to classify the genre of the game based on title of the game. The dataset I used contained two csv files; one for metacritic video game comments and the other one is the metacritic game info which is the csv file I used to classify the genre. The video game comment csv file had no genre column within in so I had to used the game info which contained the genres needed. 

The data needs to be preprocessed before we can perform the Naive bayes algorithmn. First, we apply the stop words to remove and reduce the dataset. Then, apply porter stemming which is used to trim the end of the words to find similar terms. 

{{< figure library="true" src="bayes.png" title="" lightbox="true" >}}

Naive Bayes Algorithmn:

The Naive Bayes algorithmn finds the probability of event c given the event x is true. We then calculate the conditional probabilty of our term. P(c) is our prior probability. It it the probability of the event before evidence is seen. P(c|x) is the posterior probability of x after evidence is seen. P(x) is the probability of the data. P(x|c) is the probability of data x given that the hypothesis c is true.

Contributions: 

1. Applied stopwords and stemming to reduce terms on 'Title' and 'Genre'. 

2. Applied laplace smoothing from 0.0001, 1, 10, 50, 100 to evaluate accuracy.

Challenges: 

The dataset I used did not contain any genres columns, so I had to go back to the dataset and use the other csv file which contained the genres used to classify the term. Also, since my dataset was large (250mb) hosting on pythonanywhere gave a limited amount of storage for use. So, I had to decompress or reduce the size of the dataset to use in order for storing use to be within the perimeters. 

References:

https://github.com/tungpham142/TED-Recommender

https://nlp.stanford.edu/IR-book/pdf/13bayes.pdf

https://machinelearningmastery.com/naive-bayes-classifier-scratch-python/

https://www.geeksforgeeks.org/naive-bayes-classifiers/

https://towardsdatascience.com/naive-bayes-classifier-81d512f50a7c

https://medium.com/syncedreview/applying-multinomial-naive-bayes-to-nlp-problems-a-practical-explanation-4f5271768ebf


