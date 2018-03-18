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

It involves taking word (token) counts for both positive and negative reviews. The unique token frequencies for each class are stored in dictionaries with their corresponding words as keys. These are known as *Bag of Words* (BOWs).

## Step 2: Log Likelihood and Log Prior calculation

Log of the Bayesian numerator is a sum of two values, *Log Likelihood* and *Log prior*.

Below is the equation for log likelihood:

![img](https://raw.githubusercontent.com/Tapojit/movie-review-classifier-NB/master/loglike.png)




