# Logistic Regression.
Instead of predicting exactly 0 or 1, logistic regression generates a probability—a value between 0 and 1, exclusive. For example, consider a logistic regression model for spam detection. If the model infers a value of 0.932 on a particular email message, it implies a 93.2% probability that the email message is spam. More precisely, it means that in the limit of infinite training examples, the set of examples for which the model predicts 0.932 will actually be spam 93.2% of the time and the remaining 6.8% will not.

# Calculating a Probability
The logistic regression model uses an activation function to map the intermediate real-valued prediction to a probability. The logistic function, also called the sigmoid function, satisfies the following properties:
>- Its outputs are in the range [0, 1].
>- It outputs 0.5 when its input is 0.
>- It outputs a value close to 1 when its input is large and positive.
>- It outputs a value close to 0 when its input is large and negative.

Many problems require a probability estimate as output. Logistic regression is an extremely efficient mechanism for calculating probabilities. Practically speaking, you can use the returned probability in either of the following two ways:
>- "As is"
>- As a calibration for binary classification.

A sigmoid function defined as follows:
>- $$\sigma(x) = \frac{1}{1+e^{-x}}$$
>- where:
>- $$\sigma(x)$$ 
> is the sigmoid function.
>- $$x$$  
> is the input to the function—any real number.
>- $$e$$ 
> is the base of the natural logarithm.
>- $$e^{-x}$$
> is the exponential function of $$-x$$.
>- $$\frac{1}{...}$$
> is the reciprocal of the value in the brackets.
>- $$1+...$$
> is one plus the value in the brackets.
>- $$\frac{1}{1+e^{-x}}$$
> is the sigmoid function.

# Loss and Regularization.
## Loss Function for Logistic Regression.
The loss function for linear regression is squared loss. The loss function for logistic regression is log loss, which is defined as follows:
>- $$logloss = \sum_{(x,y)\in D} [-ylog(\hat{y})-(1-y)log(1-\hat{y})]$$
>- where:
>- $$D$$
> is the data set containing $$n$$ examples.
>- $$(x,y)$$
> is an example in the data set.
>- $$\hat{y}$$
> is the predicted value.
>- $$y$$
> is the true value.
>- $$log$$
> is the natural logarithm.

## Regularization for Logistic Regression.
Regularization is extremely important in logistic regression modeling. Without regularization, the asymptotic nature of logistic regression would keep driving loss towards 0 in high dimensions. Consequently, most logistic regression models use one of the following two strategies to dampen model complexity:
>- L2 regularization
>- Early stopping
>- L1 regularization

Imagine that you assign a unique id to each example, and map each id to its own feature. If you don't specify a regularization function, the model will become completely overfit. That's because the model would try to drive loss to zero on all examples and never get there, driving the weights for each indicator feature to +infinity or -infinity. This can happen in high dimensional data with feature crosses, when there’s a huge mass of rare crosses that happen only on one example each. In this case, the model will overfit to each example, and the only way to prevent this is to use regularization.

Fortunately, using L2 or early stopping will prevent this problem. L2 regularization will drive the weights for all the rare crosses to be small but nonzero, while early stopping will prevent the model from overfitting to each example.