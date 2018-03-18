# Naive Bayes Movie Classifier

This is an implementation of a **Naive Bayes**(NB) classifier for binary classification of positive and negative sentiment
movie reviews.

Below is the *Bayes equation*, where *P(y<sub>d</sub>|w<sub>d</sub>)* is the probability that, given a document *w<sub>d</sub>*, it belongs to the class *y<sub>d</sub>*.

![img](https://raw.githubusercontent.com/Tapojit/movie-review-classifier-NB/master/Bayes.png)

While classifying movie reviews in this case, only two Bayesian probabilities need to be calculated; one for positive class and the other for negative. The review is classified as either positive or negative based on whichever probability is higher.

However, only the numerator for the Bayesian equation needs to be calculated, as *P(w<sub>d</sub>)* is same for both classes
for a given document.

To avoid numerical underflow, all probabilities are calculated in the log space.

## Step 1: Tokenization

It involves taking word (token) counts for both positive and negative reviews. The unique token frequencies for each class are stored in dictionaries with their corresponding tokens as keys. These are known as *Bag of Words* (BOWs).

## Step 2: Classification

Log of the Bayesian numerator is a sum of two values, *Log Likelihood* and *Log prior*.

Below is the equation for log likelihood:

![img](https://raw.githubusercontent.com/Tapojit/movie-review-classifier-NB/master/loglike.png)

It is the sum of log probabilities that, given a class *y<sub>d</sub>*, tokens *w<sub>d</sub><sub>i</sub>* in review *w<sub>d</sub>* belong to that class.

In certain cases, a particular token in a given review might not be present in the BOW for a given class. Probability for that token given class will be zero, which raises the issue of *log(0)*. Hence, pseudocounts(&alpha;) are added to the count of each word in the BOWs.

*Log prior* is simply the log probability of a document belonging to the *y<sub>d</sub>* class.

Based on sums of log prior and log likelihood for each class, the given review is classified as either positive or negative.

## Training Accuracy

In **NB.py**, the Naive Bayes Classifier is implemented as the object **NaiveBayes** which takes as arguments data path and tokenizer function. To train and test the classifier, in the directory of this repository, open python shell in *bash* and run the lines below: 

```
>>> from NB import *
>>> PATH_TO_DATA = 'large_movie_review_dataset'

# Initializing Classifier Object
>>> nb = NaiveBayes(PATH_TO_DATA, tokenizer=tokenize_doc)

# Training Classifier
>>> nb.train_model()

# Calculating classifier accuracy on test data with pseudocount 1
>>>  print nb.evaluate_classifier_accuracy(1.0)
```
Here is the printed output of the classifier accuracy:
```
83.028
```
