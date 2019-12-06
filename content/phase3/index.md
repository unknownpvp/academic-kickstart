

---
title: Image Recognition
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

GameLab's Image reconginition will allow user to upload an image to search for the game.

Image captioning generates the text description of images through Natural Language Processing (NLP) and Computer Vision. The dataset is used from MS-COCO which contains over 83000 images and 13GB of data. 

We download and prepare the MS-COCO dataset then, limit the size of the training set by 30,000 for faster training otherwise it would take too long. Next, the images are then preprocessed by using InceptionV3  to classify each image and extract features from the last convolutional layer. After the preprocessing and tokenizing of captions we then, split the data into training and testing which completes our images and captions. Finally, I used the MS-COCO annotation val2017 as my images to use which was 821 MB. This was ran on google colab using GPU as the runtime and to complete the entire image captioning took roughly 3 hours.

Limitations:

Some of the examples are generating incorrect captions based on the search due to the complexity of the images. 

{{< figure library="true" src="caption.png" title="" lightbox="true" >}}

Contributions:

1. For image captioning I used pickle to store my final images within the file through using google colab and implementing the json file to read in and caption the images correspondingly

Challenges:

1. I was struggling with google colab as, I have never used this before but eventually grasped the knowledge to be able to caption my images using val2017 from MS-COCO. Also, to generate the captions it took a really long time running on no runtime in which I found out that using the GPU as the runtime sped up the process significantly which went from 6 hours down to 3 hours.

2. Another challenge was downloading the MS-COCO annotations val2017 which was 821 MB in size and I failed to download the zip file due to a network error, which I was able to solve by running gsutil -m rsync gs://images.cocodataset.org/annotations [localdir]. At first, I had trouble running the gsutil command to download the dataset and I eventually figured out how to grab the neccesary file I needed by just running wget command instead with the url of the download.

References:

https://github.com/tensorflow/tensorflow/blob/r1.13/tensorflow/contrib/eager/python/examples/generative_examples/image_captioning_with_attention.ipynb

https://www.tensorflow.org/tutorials/text/image_captioning

http://cocodataset.org/#download


