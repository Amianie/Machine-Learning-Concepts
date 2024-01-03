# Validation Sets.
We have previously worked on partitioning a dataset into a training set and a test set.This partitioning enabled  us to train on one set of examples and then to test the model against a different set of examples.

Tweak model means adjusting anything about the model you can think of right from changing the learning rate, to adding or removing features,to designing a completely new model from scratch.At the end of this workflow yoy pick the model that does the best on the test data.

Use the validation set to evaluate results from the training set.Then use the test set to double-check your evaluation after the model has passed the validation set.

In this improved workflow:
>- Pick the model that does the best on the validation set.
>
>- Double-check that model against the test set.

This is a better workflow because it creates fewer exposure to the test set.