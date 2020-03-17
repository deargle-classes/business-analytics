---
title: "Lab: Avoiding Overfitting"
---

This model give hands-on experience with cross-validation. Your task is to assess the performance of three classifiers -- 
a Logistic regressor, a majority classifier, and a blender ensemble classifier. 
The models were trained on hospital record historical data with the target of predicting whether a patient would be 
readmitted to the hospital after dismissal. DataRobot was used to generate the model predictions. 
Each model was run through five-fold cross-validation, and the predictions on the entire training dataset were 
downloaded to one csv for each classifier. The downloaded datasets include one row for each record in the training data, 
with features for:

1. Whether the patient was readmitted to the hospital
2. The cross-validation prediction of probability of readmittance for that row.


The three datasets are available in the "Lab-avoiding-overfitting.yxzp" package in the "files" area of canvas. 
The three sets of predictions have been imported for you, and have been union-ed together. 


Using a tool, such as Alteryx, manually calculate the accuracy for each classifier for each cross-validation run. 
Use a prediction cutoff threshold of 0.50 to convert the readmittance probability prediction into a binary prediction. 
Because there were five folds, this will give you five rows for each classifier. Then, for each classifier, calculate 
the average accuracy as well as the standard deviation of the accuracy. This final step will give you one row for each classifier.


To calculate accuracy, you will need to do two things:

* Convert each readmittance probability prediction into a binary feature.  ex: 1 if predicted readmittance, 0 otherwise.
* Mark whether or not each prediction was correct, comparing the binary prediction against what actually happened (whether they were actually readmitted).

With the correct-or-not feature, you can then calculate accuracy.
 
**Hint:** Consider using the summarize tool to do a multi-level group-by of the output of the union on classifier id and fold id, and then calculate accuracy for each subgroup.


#### Question 1:
----------
Submit two screenshots:

1. One showing the output of your first summary tool, with a total of fifteen rows -- one for the evaluation of each x-val run in each model.
2. One showing the output of your final output somewhere after the second summary tool -- with a total of three rows -- one row per classifier, showing classifier name, average accuracy, and accuracy standard deviation.


#### Question 2:
----------
Which classifier had the highest accuracy averaged across all of its cross-validation runs?

<ol class='list-style-upper-alpha'>
    <li>AVGBlender</li>
    <li>LogisticRegression</li>
    <li>MajorityClassClassifier</li>
</ol>


#### Question 3
----------
What was the highest accuracy averaged across all of a classifier's cross-validation runs? To two decimal places, expressed in the range of 0 to 1. e.g., an accuracy of 50% should be expressed as .50


#### Question 4
----------
Which classifier had the tightest distribution of accuracies across all of its cross-validation runs?


<ol class='list-style-upper-alpha'>
    <li>AVGBlender</li>
    <li>LogisticRegression</li>
    <li>MajorityClassClassifier</li>
</ol>