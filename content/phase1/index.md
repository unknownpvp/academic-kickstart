---
title: Text Search
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

GameLab's search feature will allow the user the enter a free-text search. 

The data needs to be pre-processed first by removing stop words and using lemmatization. 
Then, an index needs to be created for our dataset. By using an inverted index, term frequency and inverse document frequency the computation weight of each word in a document can show the represenation of importance each word is in the document.

TF: Term Frequency, measures how frequently a term occurs in a document. Documents are different in length, so the terms would appear much more times in long documents than shorter ones. Then, the term frequency is divided by the document length :

{{< figure library="true" src="tf.png" title="" lightbox="true" >}}

IDF: Inverse Document Frequency, measures the importance a term is. While computing TF, all terms are considered equally important. However certain terms, such as "is", "of", and "that", may appear a lot of times but have little importance, which are stop-words that are removed at data pre-processing. So we need to weigh down the frequent terms while scale up the rare ones, by computing the following:

{{< figure library="true" src="idf.png" title="" lightbox="true" >}}

TF-IDF: Term frequency - Inverse document frequency is a weighting scheme that assigns each term in a document a weight based on its term frequency and inverse document frequency. A high weight in tf–idf is reached by a high term frequency (in the given document) and a low document frequency of the term in the whole collection of documents. The terms with higher weight scores are considered to be more important.

{{< figure library="true" src="tf-idf.png" title="" lightbox="true" >}}

Contributions: 

1. Applied nltk.corpus stopwords to reduce amount of terms in document. Removes unnecessary words that are most common such as, "the", "a", "an" etc.

2. Applied nltk.stem porterstemmer which removes the common endings from words to normalize the term.

3. Applied pickle which was used to pickle and store the dataset.

Challenges: 

The challenges I faced were that my dataset was large (250mb) and to upload it on github or pythonanywhere I had to utilize gitlfs to store the csv file. 

At first, hosting on pythonanywhere led me some difficulties because the pickled file had trouble reading a url by gitlfs. So, to overcome this challenge I had to reduce the size of the dataset and used about 100k documents. Then, I was able to get it on pythonanywhere and able to deploy the site. Also, I had to preload the data files before the user loaded the website and started the query search. 

References:

https://www.freecodecamp.org/news/how-to-process-textual-data-using-tf-idf-in-python-cd2bbc0a94a3/

https://towardsdatascience.com/tf-idf-for-document-ranking-from-scratch-in-python-on-real-world-dataset-796d339a4089

https://www.geeksforgeeks.org/tf-idf-model-for-page-ranking/
