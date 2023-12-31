# Reducing Loss

To train a model we need a good way to reduce the model's loss.Iterative approach is one of the easiest, effective and most widely used method for reducing loss.
>## An Iterative Approach.
>
>Here we are going to learn how a machine learning model iteratively reduces loss.
>
>Iteratively learning reminds us of the "Hot and Cold" kid's game for finding a hidden object like a thimble.In this game the hidden object is the best possible model.You will start with a wild guess ("The value of w<sub>1</sub> is 0) and wait for the system to tell what the loss is.Then you'll try another guess ("The value of w<sub>1</sub> is 0.5) and see what the loss is.The trick with the game is trying to find the best possible model as efficiently as possible.
>
>The following figure suggests the iterative trial-and-error process that machine learning algorithms use to train models:
>
>![img](images/Iterative%20Approach%20to%20training%20a%20model.png)
>
>The iterative approach will be used throughout the crash course,detailing various complications,particularly within that stormy cloud labeled "Model (Prediction Function)."Iterative strategies are prevalent in machine learning this is mainly because they scale so well to large datasets.
>
>The model takes one or more features as input and returns one prediction as output.Simply put,consider a model that takes one feature (x<sub>1</sub>) and returns one prediction (y'):
>
>y'=b+w<sub>1</sub>x<sub>1</sub>
>
>What initial values should we set for b and w<sub>1</sub>? for linear regression problems,it turns out that the starting values aren't important.We could pick random values, but we will just take the following trivial values instead:
>
>- b=0
>
>- w<sub>1</sub>=0
>
>Suppose that the first feature value is 10.Plugging that feature value into the prediction function yields:
>
>y'=0+0.10=0
>
>The "Compute Loss" part of the diagram is the Loss Function that the model will use.Suppose we use the squared loss function.The loss function takes in two input values:
>
>- y':The model's prediction for features X
>
>- y:The correct label corresponding to features X
>
>Now we have reached the "Compute Parameter Updates" part of the diagram.It is here that machine learning system examines the values of the loss function and generates new values for b and w<sub>1</sub>.For now just assume that this mysterious box devises new values and then the machine learning system re-evaluates all those features against all those labels,yielding a new value for the loss function,which yields new parameter values.And the learning continues iterating until the algorithm discovers the model parameters with the lowest posssible loss.Usually you iterate until the overall loss stop changing or atleast changes extremely slowly.When that happens we say that the model has **converged**.
>
>A machine learning model is trained by starting with an initial guess for the weights and bias and iteratively adjusting those guesses until learning the weights and bias with the lowest possible loss.

>## Gradient Descent
>
>The iterative approach diagram contained a green hand-wavy box entitled "Computer Parameter updates".We'll now replace that algorithmic fairy dust with something more susbstantial.
>
>Suppose we had the time and the computing resources to calculate the loss for all possible values of w<sub>1</sub>.For the kind of regression problems we've been examining the result plot of loss vs w<sub>1</sub> will always be convex.In other words, the plot will always be bowl-shaped,Example:
>
>![img](images/Regression%20problems%20yield%20convex%20loss%20vs%20weight%20loss.png)
>
>Convex problems have only one minimum and that is only one place where the slope is exactly 0.That minimum is where the loss function converges.
>
>Calculating the loss function for every conceivable value of w<sub>1</sub> over the entire dataset would be an efficient way of finding the convergent point.We can examine a better mechanism which is very popular in machine learning called gradient descent.
>
>The first stage in gradient descent is to pick a starting value for w<sub>1</sub> .The starting point does not matter that much therefore many algorithms simply set w<sub>1</sub> to 0 or pick a random value.For Example the figure below shows that the starting point picked is greater than 0.
>
>![img](images/Starting%20point%20for%20gradient%20descent.png)
>
>The gradient descent algorithm then calculates the gradient of the loss curve at the starting point.In the above diagram the gradient of the loss is equal to the derivative (slope) of the curve and tells you which way is "warmer" or "colder".When there are multiple weights,the gradient is a vector of partial derivatives with respect to the weights.
>
>Tensorflow handles all gradient computations.
>
> In machine learning,partial derivatives are mostly used in conjuction with the gradient of a function.
>
>In machine learning gradients are used in gradient descent.We often have a loss function of many variables that we are trying to minimize and we try to this by following the negative of the gradient of the function.
>
>The gradient is a vector and so it has the following characteristics:
>
>- Magnitude
>
>- direction.
>
>The gradient always points in the direction of the steepest increase in the loss function.The gradient desent algorithm takes a step in the direction of the negative gradient inorder to reduce loss as quickly as possible.
>
>![img](images/Gradient%20descent%20relies%20on%20negative%20gradients%20.png) 
>
>To determine the next point along the loss function the gradient descent algorithm adds some fraction of the gradient's magnitude to the starting point as illustrated below:
>
>![img](images/Gradient%20step%20moves%20us%20to%20the%20next%20point%20on%20the%20loss%20curve.png)
>
>The gradient descent repeats this process edging over closer to the minimum.
>

>## Learning Rate
>
> As illustrated above the gradient descent has both the direction and the magnitude.Gradient descent algorithm multiply the gradient by a scalar known as the learning rate(step size) to determine the next point.
>
>Hyperparameters are the knob that programmers tweak in machine learning algorithms.Most Machine learning programmers spend a fair amount of time tuning the learning rate.If you pick a learning rate that is too small learning will ake longer.
>
>![img](images/Learning%20rate%20is%20too%20small.png)
>
>Also if you pick a learning rate that is too large,the next point will perpetually bounce harpharzadly and everything goes wrong.
>
>There is a Goldilocks learning rate for every regression problem.The Goldilocks value is related to how flat the loss function is.If you know the gradient of the loss function is small then you can safely try a larger learning rate,which compensates for the small gradient and results in a larger step size.
>
>![img](images/Learning%20rate%20is%20just%20right.png)


>## Stochastic Gradient Descent.
>
>In gradient descent a batch is a set of examples you use to calculate the gradient in a single training iteration.A batch can be enormous.A very large barch may cause even a single iteration to take a very long time to compute.
>
>A large dataset with randomly sampled examples probably contain redundant data.Infact redundancy becomes more likely as the batch size grows.Some redundants can be useful to smooth out noisy gradients,but ernomus batches tend not to carry much more predictive value than large batches.
>
>By choosing examples at random from our dataset, we could estimate(albeit,noisily) a big average from a much smaller one.***Stochastic Gradient Descent (SGD)*** takes this idea to the extreme-- it uses only a single example (batch size of 1) per iteration.Given enough iterations,SGD works but it is very noisy.The term "Stochastic" indicates that the one example comprising each batch is chosen at random.
>
>Mini-batch Stochastic Gradient Descent.It is a compromise between full batch iteration and SGD.A min-batch is typically between 10 and 1,000 examples chosen at random.Mini-batch SGD reduces the amount of Noise in SGD but is still more efficient tha full batch.
