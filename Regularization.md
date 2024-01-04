# Regularization For Simplicity.
Regularization means penalizing the complexity of a model to reduce overfitting.

## L<sub>2</sub> Regularization
One can have a model in which the training loss gradually decreases, but the validation loss eventually increases. This phenomenon is called overfitting. Overfitting occurs when a model learns the detail and noise in the training data to the extent that it negatively impacts the performance of the model on new data. Specifically, overfitting occurs when a model is excessively complex, such as having too many parameters relative to the number of observed training data. Overfitting can be prevented by constraining the model parameters.

Channelling our inner Ockham,perhaps we could prevent overfitting by penalizing complexity. That is, we could modify our loss function to penalize large weights. This approach is called regularization.

That is instead of aiming to minimize loss (empirical risk minimization):
>- minimize(loss(Data|Model))

We will now minimize loss+complexity (structural risk minimization):
>- minimize(loss(Data|Model)+complexity(Model))

Our training optimization algorithm is now a function of two terms: the loss term, which measures how well the model fits the data, and the regularization term, which measures model complexity. The regularization term is a function of the model parameters. The regularization term is typically a function of the norm of the weights.

Ways to think of model complexity:
>- The number of features with nonzero weights.
>- The magnitude of the weights.

If model complexity is a function of weights, a feature weight with a high absolute value is more complex than a feature weight with a low absolute value. Thus, we can reduce model complexity by encouraging weights to be small. We can do this by adding to the loss function a term called the L<sub>2</sub> regularization penalty.

We can quantify complexity using the L2 regularization formula, which defines the regularization term as the sum of the squares of all the feature weights:
>- L<sub>2</sub> regularization penalty = Σ<sub>i</sub> w<sub>i</sub><sup>2</sup>
>
>where:
>- w<sub>i</sub> is the weight of a feature.
>- Σ<sub>i</sub> w<sub>i</sub><sup>2</sup> is the sum of the squares of all the feature weights.
>- L<sub>2</sub> is a constant that controls how much to penalize the weights.
>- L<sub>2</sub> regularization is also called weight decay.
>
>In this formula, weights close to zero have little effect on model complexity, while outlier weights can have a huge impact.

The L<sub>2</sub> regularization penalty term is a function of the weights. The constant L<sub>2</sub> controls the relative importance of the regularization term versus the loss term. L<sub>2</sub> is called a hyperparameter because it is not determined by the model training process. Instead, L<sub>2</sub> must be set experimentally using a validation data set or by using cross-validation.

# Lambda
Model developers tune the overall impact of the regularization term by multiplying its value by a scalar known as lambda (also called the regularization rate). That is, model developers aim to do the following:
>- $$ minimize(loss(Data|Model)+[\lambda]complexity(Model))$$

Performing L<sub>2</sub> regularization has the following effects on a model:
>- Encourages weight values toward 0 (but not exactly 0).
>- Encourages the mean of the weights toward 0, with a normal (bell-shaped or Gaussian) distribution.

Increasing the lambda value strengthens the regularization effect. Extremely large lambda values may cause the model to become underfit because the model will be penalized too heavily for its weights.Hence your model will not learn enough about the training data to make useful predictions.

Lowering the lambda tends to yield a flatter histogram. This means that the model is less sensitive to the weights, which can lead to overfitting.Hence your model will learn too much about the particularities of the training data and will not be able to generalize to new data.

The ideal value of lambda produces a model that generalizes well to new, previously unseen data. Unfortunately, that ideal value of lambda is data-dependent, so you'll need to do some tuning.