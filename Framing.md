# FRAMING

This module investigates how to frame a task as a machine learning problem,and covers many of the basic vocabulary terms shared across machine learning methods.

# Supervised Machine Learning

We are learning on how to combine inputs that produce useful predictions even on unseen data.

# Terminology

>### Label
>
> This is the variable we are predicting it is normally represented by the variable y
>
>Examples: We have a particular instance of data,X
>
>Labeled example:It has {Feature,label}:(X,Y).This is normaly used to train the model.
>
>Unlabeled example:It has {feature,?}:(X,?).This is normally used for making prediction on new data.

>### Features
>
> The way that we represent our data or the input variables describing our data.It is normally represented by variables {X<sub>1</sub>,X<sub>2</sub>,...,X<sub>n</sub>}Feaures may be drawn as say words from an email and any other source that we can use to extract information from.

>### Model
>
>Maps examples to predicted labels:Y<sup>1</sup>.Defined by internal parameters which are learned.It is also defines the relationship between features and label.
>
>Training refers to creating or learning the model.That is you show the model labeled examples and enable the model to gradually learn the relationships between features and label.
>
>Inference refers to applying the trained model to unlabeled examples.That is you use the trained model to make useful predictions.
>
>Regression Model predicts continous values.eg. The model can be used to predict questions such as 
>
>- What is the value of a car in Kenya?
>
>- What is the probability that Ruto will win for a second term in office?
>
> A classification model predicts discrete values.It can predict questions such as:
>
>- Is a given link secure or not?
>
>- Is this an image of a cat,cow or pig?

# Convenient Loss function for Regression.

L<sub>2</sub> Loss for a given example is called squared error.This is the square of the difference between prediction and label that is (observation-prediction)<sup>2</sup>

When training a model we do not care about minimizing loss on just one example but we care about minimizing loss across our entire dataset.
>#### Defining L<sub>2</sub> Loss on a Dataset.
>
>L<sub>2</sub>Loss=$\sum_{(x,y)\in D}(y-prediction(x))^2$
>
>$\sum$ : We are summing over all examples in the training dataset.
>
>***D*** :Sometimes useful to average over all examples,so divided by ||D||

## Linear Regression Example.

Using a Dataset of Chirps-per-minute and Temperature.What we will try to do is to learn a model to predict the relationship

> First Examine the data by plotting.
>
>![img](images/Chirps-per-minute%20vs%20temperature%20in%20Celsius.png)
>
> The plot above shows the temperature rising with the number of chirps.Since the relationship between chirps and temperature are linear we could draw a  straight line like below to approximate the relationship.
>
>![img](images/A%20linear%20Relationship.png)
>
>The line does not pass through all the dots but the line does clearly show the relationship between chirps and temperature.Using the equations for a line we could write down the relationship as follows:
>
>y=mx+b 
>
>but by convention of machine learning you will write the equation for a model slightly different: 
>
> y'=b+w<sub>1</sub>x<sub>1</sub>
>
>where:
>
>- y' is the predicted label (a desired output)
>
>- b is the bias(y-intercept)sometimes reffered to as w<sub>0</sub>
>
>- w<sub>1</sub> is the weight of feature 1.Weight is the same concept as the ***"slope"*** m in the traditional equation of a line.
>
>- x<sub>1</sub> is a feature (a known input) 
>
>To predict the temperature y' for a new chirps-per-minute,just substitute the x<sub>1</sub> value into this model.
>
>A more sophisticated model might rely on multiple features each having separate weights e.g 
>
>- y'=b+w<sub>1</sub>x<sub>1</sub>+w<sub>2</sub>x<sub>2</sub>+w<sub>3</sub>x<sub>3</sub>

## Training and Loss

Training a model refers to determining good values for all the weights and the bias from labeled examples

>Empirical risk minimization-this refers to a process that is done in supervised learning where a machine learning algorithm builds a model by examining many examples and attempting to find a model that minimizes loss.

>Loss on the other hand is a penalty for bad prediction.Loss is a number predicting how bad the model's prediction was on a single example.If the model's prediction is perfect the loss is zero otherwise the loss is greater.The main aim of training is to find a set of weights and biases that have low loss,on average across all examples
>
>##### Squared Loss:A populas Loss functions.
>
>We have already disscused about the squared loss above but we will only add on the Mean Square Error.
>
>**Mean square error**-Is the average square loss per example over the whole dataset.To calculate we need to sum up all the squared losses for individual examples and then divide by the number of examples:
>
>***MSE***=$1/_N\sum_{(x,y)\in D}(y-prediction(x))^2$
>
>where:
>
>- (x,y) is an example in which:
>
>   - x is the set of features.
>
>   - y is the example's labels.
>
>- ***prediction(x)*** is a function of the weights and bias in combination with the set of features x.
>
>D is a dataset containing many labeled examples,which are (x,y)pairs.
>
>N is the number of examples in D.
>
> Although MSE is used in machine learning it is neither the only practical loss function nor the best loss function for all circumstances.

