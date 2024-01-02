# Training and Test sets.
A test set is a data set used to **evaluate** the performance of a trained machine learning model.

Make sure that the test set fulfills the following two conditions:
>- is large enough to yield statistically meaningful results.
>
>- is representative of the data set as a whole.

Never train on test data. This is known as **data leakage**.If you are seeing surprisingly good results on your evaluation metrics it is a sign that you are actually training on your test set.