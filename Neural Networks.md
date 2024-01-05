# Neural Networks.
Neural Networks are a more sophisticated version of feature crosses.They learn the appropriate feature crosses themselves, rather than requiring the engineer to specify them. Neural networks are also capable of learning non-linear relationships between features. This is particularly useful for sparse features, which are common in real-world data sets.

"Nonlinear" means that you cannot accurately predict a label with a model of the form b+w<sub>1</sub>x<sub>1</sub>+w<sub>2</sub>x<sub>2</sub>+...+w<sub>n</sub>x<sub>n</sub>. For example, you cannot predict a house's price from its square footage alone, because the relationship is not linear. (A 1,000 square foot house that costs $150,000 is not twice as valuable as a 500 square foot house that costs $75,000.) However, you can predict a house's price from its square footage and its number of bedrooms, because the relationship is roughly linear. (A 1,000 square foot house with 2 bedrooms is roughly twice as valuable as a 500 square foot house with 1 bedroom.).In other words the decision surface is not a line.

## Activation Functions.
To model a nonlinear problem, we can directly introduce a nonlinearity. We can pipe each hidden layer node through a nonlinear function.

The nonlinear function is call the Activation function. The activation function is applied to the weighted sum of the inputs to the node. The result is the node's output.

Stacking nonlinearities on nonlinearities lets us model very complicated relationships between the inputs and the predicted outputs. In brief, each layer is effectively learning a more complex, higher-level function over the raw inputs. This is why neural networks are often referred to as "deep learning" models: they learn a deep hierarchy of functions.

Common Activation Functions:
- ReLU (Rectified Linear Unit) - The most common activation function in deep learning, due to its simplicity and effectiveness.$$ReLU(x) = max(0,x)$$
- Sigmoid - A common activation function in the early days of neural networks. $$Sigmoid(x) = \frac{1}{1 + exp(-x)}$$

The superiority of ReLU is based on empirical findings, probably driven by ReLU having a more useful range of responsiveness. A sigmoid's responsiveness falls off relatively quickly on both sides.

In fact, any mathematical function can serve as an activation function. Suppose that $\sigma$
 represents our activation function (Relu, Sigmoid, or whatever). Consequently, the value of a node in the network is given by the following formula:
 > $$\sigma(w \cdot x + b)$$

 TensorFlow provides out-of-the-box support for many activation functions. You can find these activation functions within TensorFlow's list of wrappers for primitive neural network operations. That said, we still recommend starting with ReLU.

A model has the following components of what we mean when we say "neural network":
>- A set of nodes,analogus to neurons, organized in layers.
>- A set of weights representing the connections between each neural network layer and the layer beneath it. The layer beneath may be another neural network layer, or some other kind of layer.
>- A set of biases, one for each node.
>- An activation function that transforms the output of each node in a layer. Different layers may have different activation functions.
