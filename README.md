# Book genre classifier using cover pages 

**Test on your own book covers using the [web app](https://book-genre-detector.onrender.com/)**.

---
*For a detailed explanation of the project, visit my [blog page](https://medium.com/swlh/judging-a-book-by-its-cover-the-deep-learning-way-94847c7c1274) !*

---

This is an end to end project that predicts the genre of any book by looking at its cover page into one of five categories - 
* Children
* Sci-fi
* Horror
* Romance
* Political

Implementation is done using the FastAI framework that is built on top of PyTorch. I have used this particular framework because it gave me a good way to clean my data that was scraped out of Google Images, which would have been a lot of work otherwise. Also, FastAI provides state of the art results with high computational power. 

### Data Preparation

For this project, I have scraped about 2500 images of book cover pages from Google Images using the following JS code:
```
urls = Array.from(document.querySelectorAll('.rg_i')).map(el=> el.hasAttribute('data-src')?el.getAttribute('data-src'):el.getAttribute('data-iurl')); 
window.open('data:text/csv;charset=utf-8,'+escape(urls.join('\n')));

```
Steps to do this :
1. Go to Google Images and search for the kind of images you want.
2. After the page opens, right click and go to the ‘Inspect’ option that is provided in Google Chrome.
3. In the console section, type in the above JS code.

This downloads the image urls in a .csv file to the default path in your system. In this way, we download the five .csv files for the five categories of images that we are going to predict. 

**The above scrapper JS code is taken from fastai's [lesson2-download.ipynb](https://github.com/fastai/course-v3/blob/master/nbs/dl1/lesson2-download.ipynb).**

A sample batch of images looks like :

![sample batch of images][logo]

[logo]: https://github.com/adityarc19/Book-Genre-classifier/blob/master/images/Screenshot%202020-07-13%20at%2010.36.57%20PM.png


### Model

For the model, I have used transfer learning, particularly a ResNet34 network. At first, I have used my input image data on the pre-trained layers and then un-trained all of them to train them again from scratch to see which approach gives better results. 
Their is a lot of data cleaning performed before starting to build the model because it had a lot of noisy and uncorrect data. Finally, I have experimented with multiple hyperparameter tunings to finally come up with the best model fit for our data.

And the final result that I got is:

![training accuracy][p]

[p]: https://github.com/adityarc19/Book-Genre-classifier/blob/master/images/WhatsApp%20Image%202020-07-14%20at%2012.38.41%20AM.jpeg

So I got an accuracy of **98.7%** which is pretty amazing considering that our data was randomly scraped from Google Images which was very unclean.

### Evaluation

To evaluate the model's performance, a confusion matrix comes in very handy.

![confusion matrix][pic]

[pic]: https://github.com/adityarc19/Book-Genre-classifier/blob/master/images/Screenshot%202020-07-14%20at%2012.27.01%20AM.png

The top wrong predictions:

![top wrongs][tw]

[tw]: https://github.com/adityarc19/Book-Genre-classifier/blob/master/images/Screenshot%202020-07-14%20at%2012.48.37%20AM.png

Clearly, the model got most confused between horror and sci-fi book covers as it predicted 3 horror books to be of sci-fi genre. This is understandable because many a time the cover page images of both these genres look very similar and ambiguous even to a human eye to discriminate.

---
---
