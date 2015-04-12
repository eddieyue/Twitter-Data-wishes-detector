Twitter Data
============

I use the Twitter data from Data Access Layer(DAL) https://github.com/cioc/DAL, which is a library that makes it easy to use the datasets. 

For this project, I work with the Twitter 'wishes' dataset, which is made up of tweets from around New Year's Day, 2013. 

The following bit of simple code to show how to extract and display them.

```python
from DAL import create

# Create a handle to the Twitter wishes dataset
wishes_labelled=DAL.create("wishes-labelled")

# Load all labelled tweets, returns the subsets of this dataset that are available
wishes_labelled.subsets()

# Yields every tweet in the given subset.
wishes_labelled.iter(subset:str)-> iterable(dict(text:str,id:str,label:str))

# Measures the classification accuracy of the given dictionary of tweet classes.
wishes_labelled.eval(dict(keys:tweet_id,values:str))->float
```

Generate Features
=================

In order to represent every tweet in a quantitative way, I build up a dictionary contains the words parsing from whole tweet dataset but exclude the extremely rare and common items. Then I  express each tweet as a binary vector according to whether has the word from dictionary I have build. Therefore, I have a bunch of very sparse vectors as each tweet has very few words.

Build a "wish detector"
=======================

Train L2 regularization logistic regression classier with on the entire set of tweets using stochastic gradient descent as "wish detector". 

Due to the premission to the data, there are some errors in notebook and the error rate plot is missing.  I will fix it as soon as I get the permission to access the data.

Please check the notebook here for detail:

http://nbviewer.ipython.org/github/eddieyue/Twitter-Data-wishes-detector/blob/master/Twitter%20Data%2C%20wishes%20detector.ipynb