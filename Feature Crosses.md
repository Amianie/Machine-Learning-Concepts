# Feature Crosses
A feature cross is a synthetic feature formed by multiplying (crossing) two or more features. Crossing combinations of features can provide predictive abilities beyond what those features can provide individually.

To slve nonlinear problems, you can add crosses of features. For example, if you have two features, A and B, you can cross them to create a third feature, A x B. If you have three features, A, B, and C, you can cross them to create the features A x B, A x C, and B x C. You can continue this process for as many features as you like.
For example let's create a feature named x<sub>3</sub> by crossing the features x<sub>1</sub> and x<sub>2</sub>:
> x<sub>3</sub> = x<sub>1</sub> x x<sub>2</sub>

We treat this newly minted feature x<sub>3</sub> just like any other feature in our model. That is, we can compute the following:
> y = w<sub>1</sub> x<sub>1</sub> + w<sub>2</sub> x<sub>2</sub> + w<sub>3</sub> x<sub>3</sub> + b

A linear algorithm can learn the weight for w<sub>3</sub> just as it would for w<sub>1</sub> and w<sub>2</sub>. Although w<sub>3</sub> encodes nonlinear information,you do not need to change how the linear model trains to determine the value of w<sub>3</sub>.

Kinds of feature crosses:
>- [A x B](): The cross of feature A and feature B.That is two values.
>- [A x B x C](): The cross of feature A, feature B, and feature C.That is three values.
>- [A x A](): The self-cross of feature A. That is one value.
>- [A x B x C x D](): The cross of feature A, feature B, feature C, and feature D. That is four values.
>- [A x A x B](): The cross of feature A, feature A, and feature B. That is three values.
>- [A x [B x C]](): The cross of feature A, the cross of feature B and feature C. That is three values.
>- [A x [B x C x D]](): The cross of feature A, the cross of feature B, feature C, and feature D. That is four values.
>- [A x B x C x D x E](): The cross of feature A, feature B, feature C, feature D, and feature E. That is five values.

Thanks to stochastic gradient descent, linear models can be trained efficiently. Consequently, supplementing scaled linear models with feature crosses has traditionally been an efficient way to train on massive-scale data sets.

## Crossing One Hot Vectors.
In practice, machine learning models seldom cross continuous features. However, machine learning models do frequently cross one-hot feature vectors. Think of feature crosses of one-hot feature vectors as logical conjunctions. For example, suppose we have two features: country and language. A one-hot encoding of each generates vectors with binary features that can be interpreted as country=USA, country=France or language=English, language=Spanish. Then, if you do a feature cross of these one-hot encodings, you get binary features that can be interpreted as logical conjunctions, such as:
> ```country:USA AND language:English```

Linear learners scale well to massive data. Using feature crosses on massive data sets is one efficient strategy for learning highly complex models. Neural networks provide another strategy.