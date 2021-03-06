# SVM

## To run locally

Simply install sklearn and numpy and you should be good to go. On windows if you have pip installed you can run `pip install sklearn` and `pip install numpy`.

## Test.py

In the test.py file there are three parameters you can play with:

**size_labeled** :
This is how many samples you wish to train the data on. In this case `1 <= size_labeled <= 300000` since our training set contains 300000 labeled samples. This allows us to reduce the size of the training set for faster results and also allows us to use part of the pre-labeled data as test data.

**size_test** :
If you are not using the full training set and you wish to use a chunk of the remaining data then you can input the number of samples you want to use as test samples here.
This is useful for testing the accuracy of the method as the samples in the train-io.txt are labeled.
In this case `size_test <= (300000 - size_labeled)`

**c** :
Here c is the penalty parameter, which represents misclassification or error term. The misclassification or error term tells the SVM optimization how much error is bearable. This is how you can control the trade-off between decision boundary and misclassification term. A low c makes the decision surface smooth, while a high c aims at classifying all training examples correctly.

#### Output of test.py

This will print to console the predicted labels, followed by the actaul labels, followed by the percentage of labels correctly guessed. _Note_ I removed my homemade accuracy function as it wasn't as accurate as I hoped. It still exists in KNN and DTC pending tests.

#### Results from test.py

1. The first thing I noticed here was that adjusting the c value didn't make much of a difference.

2. I also noticed that as I used more labeled samples the more often the classifier would predict 1 as the result.

3. The other results are as follows :
   - With 300 labeled samples used to train the classifier and a c value of 1, 49/100 labels were correctly predicted at an accuracy of 49%
   - With 300 labeled samples used to train the classifier and a c value of 50, 48/100 labels were correctly predicted at an accuracy of 48%
   - With 300 labeled samples used to train the classifier and a c value of 100, 48/100 labels were correctly predicted at an accuracy of 48%
   - With 10000 labeled samples used to train the classifier and a c value of 1, 480/1000 labels were correctly predicted at an accuracy of 48%

I couldn't go any further than this as I am working off of a 7 year old laptop, I left it overnight to try train using 100000 samples and predict the last 1000 but it failed to return anything.

## Main.py

Running the main.py file will train the classifer (clf) on the entire training set ( totalt of 300000 samples from `train-io.txt`).
It will then attempt to predict the labels for the samples in `test-in.txt` and will output the results to file called `test.out.txt`, with each label on its own line.

## Issues

- The SVM is extremely slow in comparison to other methods.
- The optimal C value and how to find it is elusive to me right now.
