# Training Neural Networks.
Backpropagation is the most common training algorithm for neural networks. It makes gradient descent feasible for multi-layer neural networks. TensorFlow handles backpropagation automatically, so you don't need a deep understanding of the algorithm. However, it's still useful to understand the intuition behind it.

## Best Practices.
The number of common ways for back propagation to go wrong:
>- Vanishing Gradients.
>- Exploding Gradients.
>- Dead ReLU Units.

>### Dropout Regularization
> 
>Yet another form of regularization, called Dropout, is useful for neural networks. It works by randomly "dropping out" unit activations in a network for a single gradient step. The more you drop out, the stronger the regularization:
>- 0.0 means no dropout regularization.
>- 1.0 means drop out all activations hence the model learns nothing.
>- Values between 0.0 and 1.0= More useful.
