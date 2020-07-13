# Book genre classifier using cover pages 

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

A sample batch of images looks like :

![sample batch of images][logo]

[logo]: https://github.com/adityarc19/Book-Genre-classifier/blob/master/images/Screenshot%202020-07-13%20at%2010.36.57%20PM.png

For the coding environment, I have used Google Colab as it provides free GPU support that is essential for such deep learning projects.

### Model
For the model, I have used a ResNet34 network. At first, I have used my input image data on the pre-trained layers and then un-trained all of them to train them again from scratch to see which approach gives better results. 
















For a detailed explaination of the model, visit my [blog page](https://medium.com/swlh/judging-a-book-by-its-cover-the-deep-learning-way-94847c7c1274) !

Test on your own book covers using the [web app](https://book-genre-detector.onrender.com/).
