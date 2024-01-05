# Static Vs Dynamic Training
A static model is trained offline. That is, we train the model exactly once and then use that trained model for a while.

A dynamic model is trained online. That is, data is continually entering the system and we're incorporating that data into the model through continuous updates.

# Static VS Dynamic Inference
offline inference, meaning that you make all possible predictions in a batch, using a MapReduce or something similar. You then write the predictions to an SSTable or Bigtable, and then feed these to a cache/lookup table.

online inference, meaning that you predict on demand, using a server.

# Data Dependencies.
Some of the questions to ask in order to make sure that your input data will give you correct output:
>### Reliability
>
>Some of the questions to ask about the reliability of your data:
>- Is the signal always going to be available or is it coming from an unreliable source? eg
>   - Is the signal coming from a server that crashes under heavy load?
>   - Is the signal coming from humans that go on vacation every August?

>### Versioning
>
>Some questions to ask about Versioning:
>- Does the system that computes this data ever change? If so:
>   - How often does it change?
>   - How do you know when it changes?
>
>Sometimes, data comes from an upstream process. If that process changes abruptly, your model can suffer.
>
>Consider creating your own copy of the data you receive from the upstream process. Then, only advance to the next version of the upstream data when you are certain that it is safe to do so.

>### Neccesity
>
> These questions will remind you about regularization:
>- Does the usefulness of the feature justify the cost of including it?
>
>It is always tempting to add more features to the model. For example, suppose you find a new feature whose addition makes your model slightly more accurate. More accuracy certainly sounds better than less accuracy. However, now you've just added to your maintenance burden. That additional feature could degrade unexpectedly, so you've got to monitor it. Think carefully before adding features that lead to minor short-term wins.

>### Corelations
>
>Some features correlate (positively or negatively) with other features. Ask yourself the following question:
>- Are any features so tied together that you need additional strategies to tease them apart?

>### Feedback Loops
>
>Sometimes a model can affect its own training data. For example, the results from some models, in turn, are directly or indirectly input features to that same model.
>
>Sometimes a model can affect another model. For example, consider two models for predicting stock prices;
>- Model A, which is a bad predictive model.
>- Model B
>
>Since Model A is buggy, it mistakenly decides to buy stock in Stock X. Those purchases drive up the price of Stock X. Model B uses the price of Stock X as an input feature, so Model B can easily come to some false conclusions about the value of Stock X stock. Model B could, therefore, buy or sell shares of Stock X based on the buggy behavior of Model A. Model B's behavior, in turn, can affect Model A, possibly triggering a tulip mania or a slide in Company X's stock

# Fairness
>### Types of Bias;
>- Reporting Bias.
>- Automation Bias.
>- Selection Bias.
>   - Coverage Bias.
>   - Non-response Bias.
>   - Sampling Bias.
>- Group Attribution Bias.
>  - In-group Bias.
>  - Out-group Homogeneity Bias.
>- Implicit Bias.


>### Identifying Bias.
>
>Here we are looking at some of the potential sources of Biases:
>- Missing Feature Values.
>- Unexpected Feature Values.
>- Data Skew.

