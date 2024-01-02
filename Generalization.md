# Generalizations
Generalization refers to your model's ability to dapt properly  to new previously unseen data, drawn from the same distribution as the one used to create the model.

## Peril of Overfitting
An overfit model gets a low loss during training but does a poor job predicting new data.If a model fits the current sample,well how can we trust that it will make good predictions on new data?

Overfitting  is caused by making a model more complex than necessary. The fundamental tension of machine learning is between fitting our data well, but also fitting the data as simply as possible.

Machine Learning's goal is to predict well on new data drawn from a (hidden) true probability distribution. But we can't see that distribution directly. We only have a limited sample of data from it. The fundamental tension of machine learning is between fitting our data well, but also fitting the data as simply as possible. If we make our model too complex, it can have a hard time generalizing to new data, a problem known as overfitting.

To put Ockham's razor in machine learning terms: prefer simpler models over complex ones. Simpler models are less likely to overfit than complex ones.The less an ML model the more likely that a good empirical result is not just due to the peculiarities of the sample.

Today we have formalized Ockham's razor into the field of statistical learning theory, which shows that the best predictor of out-of-sample error is the model's performance on the training data. That is, to reduce generalization error, we must reduce the gap between training and test performance.We have also done so in the field of Computational Learning Theory.These field  have developed generalization bounds -- a statistical description of a model's ability to generalize to new data based on factors such as :
>- The complexity of the model.
> 
>- The model's performance on training data.

While the theoretical analysis provides formal guarantees  under idealized assumptions,they can be difficult to apply in practice.This course focuses on emprircal evaluation to judge a model's ability to generalize to new data.

A machine learing model aims to make good predictions on new,previously unseen data.But if you are building a model from your dataset, how would you get the previously unseen data? One way is to divide your dataset into two subsets :
>- **Training set**- a subset to train our dataset.
>
>- **Test set**-a subset to test the model.

Good performance on the test is a useful indicator of good performance on the new data in general,assuming that:
>- The test set is large enough.
>
>- You do not cheat by using the same test over and over again.

## The ML Fine Print.
The following three basic assumptions guide generalization:
>- We draw examples Independently and Identically(I.I.d) at random from the distribution.It simply means that examples do not influence each other.(An alternate explanation:i.i.d is a way of referrinn randomness of variables.)
>
>- The distribution is stationary; the distribution does not change within the data set.
>
>- We draw examples from partitions from the same distribution.

In practice we somehow violate these assumptions example:
>- Consider a model that chooses ads to display.The i.i.d assumption would be violated if the model bases its choice of ads, on what ads the user has previously seen.
>
>- Consider a data set that contains retail sales information for a year.User's purchases change seasonally,which will violae stationarity.

When we know that any of the preceeding three basic assumptions are violated,we must pay carefull attention to metrics.


