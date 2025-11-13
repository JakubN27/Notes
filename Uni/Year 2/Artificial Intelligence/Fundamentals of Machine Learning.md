# Defining Machine Learning
Machine learning is the design and study of software artifacts that use past experience to inform future decision; machine learning is the study of programs that learn from data. The fundamental goal is to generalise or to induce an unknown rule from examples of the rules application.

## Supervised Learning
In supervised learning problems, a program predicts an output for an input y learning from pairs of labelled inputs and outputs. That is, the program learns from examples of the 'right answers'.

## Unsupervised Learning
In unsupervised learning, a program does not learn from labelled data. Instead it attempts to discover new patterns in the data.

## Reinforcement Learning
In reinforcement learning, the program receives feedback for its decisions, and errors are not explicitly corrected, and it iterates until a certain accuracy is obtained.

# Machine Learning Tasks
Two of the most common supervised machine learning tasks are **classification** and **regression**.

## Classification
In classification tasks, the program must learnt to predict discrete values for one or more response variables from one or more features. That is, the program must predict the most probably category, class or label for new observations.

## Regression
In regression problems, the program must predict values of one or more continuous response variables from one or more features.

Common unsupervised learning tasks are **clustering** and **dimensionality reductions**

## Clustering
The task of clustering is to discover groups of related observations, called clusters, within the dataset. This task, called clustering or cluster analysis, assigns observations into groups such that observations within a groups are more similar to each other based on some similarity measure than they are to observations in other clusters. Clustering is more commonly used to explore a dataset.

## Dimensionality Reduction
Dimensionality reduction is the process of discovering features which account for the greatest changes in the response variable. It can also be used to visualise data. It is easy to visualise a regression program such as predicting the price of a home from its size, but as more variables are added it becomes impossible for a human to visualise.

# Types of Data
## Training Data
A training set is a collection of observations. These observations comprise the experience that the algorithm uses to learn. In supervised learning problems, each observation consists of an observed response variable and features of one or observed explanatory variables. 

## Test Data
The test set is a similar collection of observations. The test set is used to evaluate the performance of the model using some performance metric. It is important that no observations from the training set are included in the test set. If they are, it will be difficult to asses whether the algorithms has learned to generalize from the training set or has simply memorised it, A program which has generalised, deals well with new data, while one that has memorised does not. Memorising the training set is called over-fitting. It can also risk the model memorising relations which are purely coincidental in the training set. This problem can be solved using **regularisation**.

## Validation Data
The validation set is used to tune variables called hyper parameters, which control how the algorithm learns from the training data. The program is still evaluated on the test set to provide an estimate of its performance in the real world. The validations set should not be used to estimate real world performance because the program has been tuned to learn from the training data in a  that optimises its score on the validation data, but the program will not have this advantage in the real world.

It is common to partition a single set of supervised observation into training, validation and test sets. There are no requirements for the sizes of the partitions and they may vary based on the data available. Commonly we use:
- 50-75% of the data for the **training set**
- 10-25% of the data for the **test set**
- And the remainder for the **validation set**

## Quality of Data Sets
Generally, the amount of data correlates with the quality of the model trained upon it, but quality of data matters too, since noisy data can 'confuse' it and lead to inconsistent results. Many supervised training sets are prepared manually or by semi-automated processes. When training data is scarce, a practice called cross-validation is used to train and validate the model on the same data. In cross-validation the training data is partitioned, and the model is trained on all but one partition, and tested on the one. The partitions are rotated several times so that the model is trained and evaluated on all of the data. The mean of the model's scores on each of the partitions is a better estimate of performance in the real world than an evaluation using a single training/testing split.

# Bias and variance
 The two fundamental causes of prediction error are a models bias and its variance.
 A model with high bias will generally produce similar errors regardless of what training set it has used to learn. The model biases its own assumptions about the real relationship over the relationship demonstrated in the training data. A model with high variance, will produce different errors for an input depending on the training set that it used to learn. So a model with bias is inflexible, or stubborn, while a model with variance is inflexible, or indecisive.
 ![[Pasted image 20251112113911.png]]
 
Ideally a model will have low bias and low variance, but typically attempts to reduce one will increase the other. This is known as the bias-variance trade-off.