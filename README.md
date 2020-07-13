# Book genre classifier using cover pages. 

This is an end to end project that predicts the genre of any book by looking at its cover page into one of five categories - 
⋅⋅* Children
⋅⋅* Sci-fi
⋅⋅* Horror
⋅⋅* Romance
⋅⋅* Political

Implementation is done using the FastAI framework that is built on top of PyTorch. I have used this particular framework because it gave me a good way to clean my data that was scraped out of Google Images, which would have been a lot of work otherwise. Also, FastAI provides state of the art results with high computational power. 

### Data Preparation
For this project, I have scraped images of books’ cover pages from Google Images using the following JS code:
```
urls = Array.from(document.querySelectorAll('.rg_i')).map(el=> el.hasAttribute('data-src')?el.getAttribute('data-src'):el.getAttribute('data-iurl')); 
window.open('data:text/csv;charset=utf-8,'+escape(urls.join('\n')));

```

















For a detailed explaination of the model, visit my [blog page](https://medium.com/swlh/judging-a-book-by-its-cover-the-deep-learning-way-94847c7c1274) !

Test on your own book covers using the [web app](https://book-genre-detector.onrender.com/).
