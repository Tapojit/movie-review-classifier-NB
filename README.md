# Naive Bayes Movie Classifier

This is an implementation of a **Naive Bayes**(NB) classifier for binary classification of positive and negative sentiment
movie reviews.

Below is the *Bayes equation*, where *P(y<sub>d</sub>|w<sub>d</sub>)* is the probability that, given a document *w<sub>d</sub>*,
it belongs to the class *y<sub>d</sub>*. While classifying movie reviews in this case, only two Bayesian probabilities need
to be calculated; one for positive class and the other for negative. The review is classified as either positive or negative
based on whichever probability is higher.

However, only the numerator for the Bayesian equation needs to be calculated, as *P(w<sub>d</sub>)* is same for both classes
for a given document.

![img](https://raw.githubusercontent.com/Tapojit/movie-review-classifier-NB/master/Bayes.png)
