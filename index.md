---
title: Ml learning documentation blog
---

* Jeremy's fast.ai 2019 edition. Followed the video lectures and the textbook. 
  Binder doesn't work too well but I saw no reason to migrate the work to huggingface:
1. [Bear classifier example](https://github.com/mikegarts/bearsapp) 
2. [Multi category example](https://github.com/mikegarts/multicatapp)
3. [Pets example](https://github.com/mikegarts/petsapp)

* [Mit deep learning](http://introtodeeplearning.com/) course. A free and quick course with colab notebooks as exercises. 
This course one uses tensorflow.
One of the exercises included a sequential RNN to generate music based on this course. 
Here's what LSTM RNN can generate after a quick training on a few musical files and then fine tuning (transfer learning) to a genre:

1. Transfer learning to the style of Joplin 
   <audio controls> <source src="https://github.com/mikegarts/ml-blog/raw/main/resources/j_1_965.wav" type="audio/wav"> Your browser does not support the audio element. </audio>
2. Chopin Style 
   <audio controls> <source src="https://github.com/mikegarts/ml-blog/raw/main/resources/chopinpreludes_0_5550.wav" type="audio/wav"> Your browser does not support the audio element. </audio>

Approaching this using transformers would probably yield much better result.

* Coursera's Andrew Ng's machine learning specialization. 
It's a great step-by-step course with an emphasis on 'classical' regression in the beginning.
1. https://www.coursera.org/specializations/machine-learning-introduction

* [The huggingface course](https://huggingface.co/course)  
1. [Remarqify app](https://huggingface.co/spaces/mikegarts/remarqify) on huggingface. This app uses the distilgpt2 model retrained on books by Erich Maria Remarques 

* Kaggle courses:
1. [Intro](https://www.kaggle.com/learn/intro-to-machine-learning)
2. [Pandas](https://www.kaggle.com/learn/pandas)
3. [Intermediate Ml](https://www.kaggle.com/learn/intermediate-machine-learning)
4. [Data Visualization](https://www.kaggle.com/learn/data-visualization)
5. [sql](https://www.kaggle.com/learn/intro-to-sql)
6. [Deep learning intro](https://www.kaggle.com/learn/intro-to-deep-learning)
7. [Computer vision](https://www.kaggle.com/learn/computer-vision)
8. [Data Cleaning](https://www.kaggle.com/learn/data-cleaning)
9. [Geospatial](https://www.kaggle.com/learn/geospatial-analysis)
10. [Explainability](https://www.kaggle.com/learn/machine-learning-explainability)

Probably the most interesting for me was the course about explainability since it gives you a basic toolkit to 
systematically improve upon the results. 
The data visualisation (and pandas) are also a great for pandas noobs (like me).  

* Kaggle challenges:
1. Titanic intro challenge
2. [Spaceship titanic](https://www.kaggle.com/code/michaelgartsbein/spaceship-titanic/notebook) challange. My best submission got me to top 10%. 

* fastai 2022 course
1. This blog :)
2. [fastai pets](https://huggingface.co/spaces/mikegarts/fastai_pets) on huggingface 2022 edition
