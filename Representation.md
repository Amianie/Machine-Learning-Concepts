# Representation
## Feature Engineering.

In traditional programming, the focus is on code.In machine learning projects,the focus shifts to representation.That is one way developers hone a model is by addiing and improving its features.

### Mapping Raw Data to features.
The left side of Figure 1 illustrates raw data from an input data source; the right side illustrates a feature vector, which is the set of floating-point values comprising the examples in your data set. Feature engineering means transforming raw data into a feature vector. Expect to spend significant time doing feature engineering.

Many machine learning models must represent the features as real-numbered vectors since the feature values must be multiplied by the model weights.

![img](images/Feature%20Engineering%20Data%20maps%20raw%20data%20to%20ML%20Features.png)

## Mapping Numeric Values
Integer and floating-point data do not need a special encoding because they can be multiplied by a numeric weight.

## Mapping Categorical Values.
Categorical features have a discrete set of possible values. e.g. a feature named "favourite ice cream" might have the values "chocolate", "vanilla", or "strawberry". These are typically represented as strings. Since machine learning models require numeric input, you must convert categorical features to numeric values.

Since models cannot multiply strings by the learned weights,we use feature engineering to convert strings to their numeric values.

We can accomplish this by defining a mapping from the feature values which we will refer to as the vocabulary of possible values,to integers.Since not every favourite ice cream in the world will appear in our dataset we can group all other icecream flavors into a catch all "other" category known as the out-of-vocabulary(OOV) bucket.

Using this approach we can map our favourite ice cream feature to a numeric value.

However if we incorporate these index numbers into our model,it will impose some constraints that may be problematic:
>- We will be learning a single weight that applies to all ice cream flavors.
>
>- We are not accounting for cases wherea particular ice cream flavor may take multiple values.

To remove these constraints we can instead create a binary vector for each categorical feature in our model that represents values as follows:
>- for values that apply to the example,set corresponding vector elements to 1.
>
>- set all other elements to 0.

The length of this vector is equal to the number of elements in the vocabulary. This representation is called a one-hot encoding when a single value is 1, and a multi-hot encoding when multiple values are 1.

This approach effectively creates a Boolean variable for every feature value (e.g., Ice cream flavor). Here, if a flavor is on Vanilla then the binary value is 1 only for Vanilla. Thus, the model uses only the weight for Vanilla.

Similarly, if a flavor is at the other types of flavors, then two binary values are set to 1, and the model uses both their respective weights.

### Sparse Representation
Explicitly creating a binary vector of 1,000,000 elements where only 1 or 2 elements are true is a very inefficient representation in terms of both storage and computation time when processing these vectors. In this situation, a common approach is to use a sparse representation in which only nonzero values are stored. In sparse representations, an independent model weight is still learned for each feature value, as described above.

## Qualities of Good Features.
>- Avoid rarely used discrete feature values.
>- Prefer clear and obvious meanings.
>- Don't mix "magic" values with actual data.
>- Account for upstream instability.

## Cleaning Data
>#### Scaling Feature Values.
>
>Scaling means converting floating-point feature values from their natural range (for example, 100 to 900) into a standard range (for example, 0 to 1 or -1 to +1). If a feature set consists of only a single feature, then scaling provides little to no practical benefit. If, however, a feature set consists of multiple features, then feature scaling provides the following benefits:
>- Helps gradient descent converge more quickly.
>- Helps avoid the "NaN trap," in which one number in the model becomes a NaN (e.g., when a value exceeds the floating-point precision limit during training), and—due to math operations—every other number in the model also eventually becomes a NaN.
>- Helps the model learn appropriate weights for each feature. Without feature scaling, the model will pay too much attention to the features having a wider range.

You don't have to give every floating-point feature exactly the same scale. Nothing terrible will happen if Feature A is scaled from -1 to +1 while Feature B is scaled from -3 to +3. However, your model will react poorly if Feature B is scaled from 5000 to 100000.

You can handle extreme outliers using the following ways:
>- Logaritmic scaling.
>- Clipping.

## Scrubbing
Data sets are unreliable due to the following reasons:
>- Missing values.
>- Duplicate examples.
>- Bad labels.
>- Bad feature values.

Once detected, you typically "fix" bad examples by removing them from the data set. To detect omitted values or duplicated examples, you can write a simple program. Detecting bad feature values or labels can be far trickier.

In addition to detecting bad individual examples, you must also detect bad data in the aggregate. Histograms are a great mechanism for visualizing your data in the aggregate. In addition, getting statistics like the following can help:
>- Mean and Median.
>- Standard Deviation.
>- Min and Max.

## Know your Data
keep to the following rules:
>- Keep in mind what you think your data should look like.
>- Verify that your data meets your expectations or that you can explain why it doesn not.
>- Double check that the training data agrees with other sources.

Treat your data with all the care that you would treat any mission-critical code. If you don't, you will likely end up with a model that is no better than random guessing.Good ML relies on good data.





