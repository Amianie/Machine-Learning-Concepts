# Regularization for Sparsity.
Sparse vectors often contain many dimensions. Creating a feature cross results in even more dimensions. Given such high-dimensional feature vectors, model size may become huge and require huge amounts of RAM.

In a high-dimensional sparse vector, it would be nice to encourage weights to drop to exactly 0 where possible. A weight of exactly 0 essentially removes the corresponding feature from the model. Zeroing out features will save RAM and may reduce noise in the model.

However, there is a regularization term called L1 regularization that serves as an approximation to L0, but has the advantage of being convex and thus efficient to compute. So we can use L1 regularization to encourage many of the uninformative coefficients in our model to be exactly 0, and thus reap RAM savings at inference time.

## L1 vs L2 Regularization
>L<sub>2</sub> and L<sub>1</sub> penalize weights differently:
>-  L<sub>2</sub> penalizes weight<sup>2</sup>
>- L<sub>1</sub> penalizes |weight|
>
>L<sub>2</sub> and L<sub>1</sub> have different derivatives:
>- L<sub>2</sub> has a derivative of 2 * weight
>- L<sub>1</sub> has a derivative of k (a constant whose values is independent of weight)

You can think of the derivative of L<sub>2</sub> as a force that removes x% of the weight every time. As Zeno knew, even if you remove x percent of a number billions of times, the diminished number will still never quite reach zero. (Zeno was less familiar with floating-point precision limitations, which could possibly produce exactly zero.) At any rate, L<sub>2</sub> does not normally drive weights to zero.

You can think of the derivative of L<sub>1 </sub>as a force that subtracts some constant from the weight every time. However, thanks to absolute values, L<sub>1</sub> has a discontinuity at 0, which causes subtraction results that cross 0 to become zeroed out. For example, if subtraction would have forced a weight from +0.1 to -0.2, L<sub>1</sub> will set the weight to exactly 0. Eureka, L<sub>1</sub> zeroed out the weight.

L<sub>1</sub> regularization—penalizing the absolute value of all the weights—turns out to be quite efficient for wide models.