---
title: 07 - Midterm 1
---

# Analytics Topics for First Exam


## Generally
* Do not need to memorize any formulas
* Do not need to be prepared to use Alteryx, DataRobot, or any tool besides pen-and-paper for simple math calculations
* Do need to conceptually understand the principles of business analytics that we have discussed so far
* Do not need to understand principles in the book that we have not discussed in class...
   * But the book will be monumentally helpful towards your conceptual understanding of what we have discussed.


## Supplemental Book Chapters
* 1,2,3,4,5,7,11

## Conceptual from first half of class
* CRISP-DM and each of its phases
* Unsupervised vs supervised learning
* The strictly conceptual need for and use of the following for predictive analytics:
   * ETL
   * Transformations / feature engineering 
      * Joining, summarising

## Lecture: Introduction to Predictive Analytics
* Slides 2-6
* Conceptual understanding of how linear models are formulaically represented and for how predictions are made based off x-values and the weights the model assigns to each predictor
* Conceptual understanding of the need for dummy-coding for linear models, and for the use of reference levels in models with an intercept

## Lecture: Supervised Segmentation
* Conceptual understanding of the use of supervised segmentation, of information gain, of “informative attributes”, of entropy
* Ability to interpret Entropy vs Proportion plots
* Understanding of how to obtain a probability prediction of class membership from a decision tree
* Understand conceptually the need for and use of Laplace Correction
* Understand the desirability preference between a model providing predictions of discrete values versus predictions of probabilities of class membership.
* Do not need to memorize entropy formulas, information gain formulas, or the formula for laplace correction

## Lecture: Discriminant Functions
* Concept of decision boundaries, and of the ultimate goal being a probability prediction
* Concept of logistic regression, of the need for it to directly predict logOdds, of why linear functions cannot directly predict probability
* Link between probability => odds => logOdds
* Concept of SVM
* Concept of objective functions (i.e., loss functions), which linear regression uses, and which SVM uses
* How to get non-linear models from linear models
* Basic understanding of how each node in a neural network is simply an isolated model, and how outputs of previous models feed into next layer ones.

## Lecture: Model Performance
* Concept of over- and under-fitting
* How to evaluate models:
   * Options 1 (in-sample evaluation), 2 (TVH or train-validation), option 3 (x-val) and how each works
   * X-val
* Concept of decision tree pruning
* Learning Curves
* Fitting Graphs
* Concept of Regularization for linear models
   * Do not need to memorise that ridge involves summing the squares of the weights and that lasso sums the absolute weight values
   * Understand conceptually the approach of regularization
* Do not need to understand nested cross-validation
* Be familiar with general partitioning methods (e.g., random, stratified, group)

## Lecture: Decision Analytics Thinking
* Conceptually how accuracy as an evaluation metric can fail
   * We didn’t use this precise term in class, but we talked around it. Understand the concept of the “base-rate fallacy.” This is another reason why accuracy is a misleading metric.
* Concept of confusion matrices for binary class prediction evaluation:
   * The labeling of individual cells
   * The ability to create a basic matrix from simple data
   * Do need to memorise how to use a confusion matrix to obtain:
      * True Positive Rate (i.e., sensitivity, recall), 
      * False Positive Rate, and 
      * Positive Predictive Value (i.e., precision)
   * Do not need to memorize the various synonyms for the above three metrics
   * Be able to interpret probability-notation-representation of the above metrics:
      * p(Y|p) == True Positive Rate
      * p(Y|n) == False Positive Rate
      * p(p|Y) == Positive Predictive Value
* Understand the two basic uses of the Expected Value Framework, and for how a cost-benefit matrix is obtained