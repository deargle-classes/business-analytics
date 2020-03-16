---
title: 13 - CRISP-DM Project
---

# DataRobot project -- Diabetes Data

# Todo before assigning again
* Ask for f1-optimizing threshold and interpretation for management
* Give example of interpreting prediction explanations
* Ask for more explanation for lift-chart and binning
* Emphasize that all tables and figures need accompanying prose
* Give an example of what should and should not go in the data preparation vs appendix sections

# Deliverables

- This Friday midnight \| Business understanding through ... Data Preparation
    - Turn in: 
        - A word document with business understanding and data understanding
        - alteryx workflow (yxzp) showing all data preparation
- Next Tuesday Night \| ... and back to Data Understanding through Modeling
    - Turn in:
        - A word document of your draft of data descriptives plus modeling writeup
            - Show a screenshot or something of datarobot showing me your models screen
- Thursday Night \| Evaluation to End (final deliverable)
    - Turn in:
        - One word doc with the complete report -- all sections combined
        - Alteryx workflow
        - Share with david.eargle@colorado.edu your datarobot project so I can take a peek if necessary. You can share projects with your teammates, you should do that too. Please put your canvas team number in your datarobot project name!
        - Don’t forget the managerial holdout predictions, as mentioned in the report

# Sources:
* For this project, you will analyze the following data: https://archive.ics.uci.edu/ml/datasets/diabetes+130-us+hospitals+for+years+1999-2008
* The data can be downloaded here: https://archive.ics.uci.edu/ml/machine-learning-databases/00296/ 
* The features are defined as follows: https://www.hindawi.com/journals/bmri/2014/781670/tab1/ 
* The description of the data is found in this academic paper: https://www.hindawi.com/journals/bmri/2014/781670/ we will replicate the data preparation and feature engineering that the authors performed in that paper.

The paper, and the uci page, describe the data as follows:

> The dataset represents 10 years (1999-2008) of clinical care at 130 US hospitals and integrated delivery networks. It includes over 50 features representing patient and hospital outcomes. Information was extracted from the database for encounters that satisfied the following criteria.
> (1)	It is an inpatient encounter (a hospital admission).
> (2)	It is a diabetic encounter, that is, one during which any kind of diabetes was entered to the system as a diagnosis.
> (3)	The length of stay was at least 1 day and at most 14 days.
> (4)	Laboratory tests were performed during the encounter.
> (5)	Medications were administered during the encounter.
> The data contains such attributes as patient number, race, gender, age, admission type, time in hospital, medical specialty of admitting physician, number of lab test performed, HbA1c test result, diagnosis, number of medication, diabetic medications, number of outpatient, inpatient, and emergency visits in the year before the hospitalization, etc.


**Problem statement:** Management is concerned about the number of diabetic patients who are readmitted to the hospital within 30 days. If they are readmitted within 30 days, then this is a sign that proper care may not have been administered during the previous visit. If they are readmitted after 30 days, then management is less concerned about potential insufficient care. You have been asked by management to analyze the data on visits and develop a model that can predict whether a patient will be readmitted to the hospital.

You will write a report following the CRISP-DM structure. Specifically, your report should have the following sections:

* Business Understanding 5%
* Data Understanding 5%
* Data Preparation 10%
* ... and back to Data Understanding 10%
* Modeling 30%
* Evaluation 30%
* Conclusion
* Appendix – Feature Engineering and Restructuring 10% 

## Business Understanding

* In this section, describe the purpose of the project. Articulating the purpose will help you in later stages of the CRISP-DM process.
* Please do not copy-paste what I wrote above

## Data Understanding

*   In this section, describe the original datasource _before_ any data preparation. E.g., Number of rows, what each row represents, data source 
    (not just what website it came from, but where the actual data was collected from and what it looks like).
*   Please do not simply copy-paste the above

## Data Preparation

* Actually perform the following feature engineering and data cleaning. The following has quotes extracted from the research paper.
    * “Since we are primarily interested in factors that lead to early readmission, we defined the readmission attribute (outcome) as having two values: “readmitted,” if the patient was readmitted within 30 days of discharge or “otherwise,” which covers both readmission after 30 days and no readmission at all.”
    * Join admission_type_id, discharge_disposition_id, and admission_source_id onto their text descriptions (available in file “IDs_mapping.csv”)
    * “The preliminary dataset contained multiple inpatient visits for some patients and the observations could not be considered as statistically independent, an assumption of the logistic regression model. We thus used only one encounter per patient; in particular, we considered only the first encounter for each patient as the primary admission and determined whether or not they were readmitted within 30 days.”
    * “Additionally, we removed all encounters that resulted in either discharge to a hospice or patient death, to avoid biasing our analysis.”
    * Create HbA1c variable using `A1c` and `changed` columns, as follows: "We considered four groups of encounters: (1) no HbA1c test performed, (2) HbA1c performed and in normal range, (3) HbA1c performed and the result is greater than 8% with no change in diabetic medications, and (4) HbA1c performed, result is greater than 8%, and diabetic medication was changed."
    * “Diagnosis” stands for a primary diagnosis with possible values: 
        * “circulatory” for icd9: 390–459, 785, 
        * “digestive” for icd9: 520–579, 787, 
        * “genitourinary” for icd9: 580–629, 788, 
        * “diabetes” for icd9: 250.xx, 
        * “injury” for icd9: 800–999, 
        * “musculoskeletal” for icd9: 710–739, 
        * “neoplasms” for icd9: 140–239, 
        * “respiratory” for icd9: 460–519, 786, and 
        * “other” for otherwise.
    * Binning:
        * Discharge Disposition:
            * Discharged to Home
            * Otherwise
        * Admission Source
            * Admitted from Emergency Room
            * Admitted because of physician/clinic referral
            * Otherwise
        * Specialty of the admitting physician
            * Internal medicine
            * Cardiology
            * Surgery
            * family/general practice
            * Missing or unknown
            * Other
    * Use Alteryx for this preparation. Your goal is to obtain a flat csv file that you can later upload to datarobot

* In this section, describe the feature engineering that you performed, with enough detail that someone else could reproduce your work. Your report may be handed to the engineering team, and they may need to be able to reproduce what you did.
* (see notes for the appendix):
    * In the appendix, provide a supplementary Alteryx workflow with your deliverable showing all data preparation.
    * Also provide a screenshot from datarobot showing what datatypes you set for each feature
    
## ... and back to Data Understanding 10%
* In this section, provide summary statistics for each of your features, for each of the values in the table show below. Also include sample size after data preparation above.
* You should try to obtain these statistics using DataRobot. Notice in the table below that additional “binning” was undertaken on some features, including Discharge Disposition and Admission Source.
* Only fill in the yellow-highlighted cells

<table>
    <thead>
        <tr>
            <th></th>
            <th></th>
            <th></th>
            <th></th>
            <th colspan='2'>Readmitted</th>
        </tr>
        <tr>
            <th colspan='2'>Variable</th>
            <th>Number of encounters</th>
            <th>% of the Population</th>
            <th>Number of Encounters</th>
            <th>% in group</th>
        </tr>
    </thead>
    <tbody>
        <tr><th colspan='2'>HbA1c</th><td></td><td></td><td></td><td></td></tr>
        <tr><td></td><th>Not measured</th><td></td><td></td><td></td><td></td></tr>
        <tr><td></td><td>High, changed</td><td></td><td></td><td></td><td></td></tr>
        <tr><td></td><td>High, not changed</td><td></td><td></td><td></td><td></td></tr>
        <tr><td></td><td>Normal</td><td></td><td></td><td></td><td></td></tr>
        <tr><td colspan='2'>Discharge</td><td></td><td></td><td></td><td></td></tr>
        <tr><td></td><td>Home</td><td></td><td></td><td></td><td></td></tr>
        <tr><td></td><td>Other</td><td></td><td></td><td></td><td></td></tr>
        <tr><td colspan='2'>Race</td><td></td><td></td><td></td><td></td></tr>
        <tr><td></td><td>African American</td><td></td><td></td><td></td><td></td></tr>
        <tr><td></td><td>Caucasian</td><td></td><td></td><td></td><td></td></tr>
        <tr><td></td><td>Missing</td><td></td><td></td><td></td><td></td></tr>
        <tr><td></td><td>Other</td><td></td><td></td><td></td><td></td></tr>
        <tr><td colspan='2'>Admission</td><td></td><td></td><td></td><td></td></tr>
        <tr><td></td><td>Emergency</td><td></td><td></td><td></td><td></td></tr>
        <tr><td></td><td>Other</td><td></td><td></td><td></td><td></td></tr>
        <tr><td></td><td>Referral</td><td></td><td></td><td></td><td></td></tr>
        <tr><td colspan='2'>Medical Specialty</td><td></td><td></td><td></td><td></td></tr>
        <tr><td></td><td>Cardiology</td><td></td><td></td><td></td><td></td></tr>
        <tr><td></td><td>General Practice</td><td></td><td></td><td></td><td></td></tr>
        <tr><td></td><td>Internal Medicine</td><td></td><td></td><td></td><td></td></tr>
        <tr><td></td><td>Missing</td><td></td><td></td><td></td><td></td></tr>
        <tr><td></td><td>Other</td><td></td><td></td><td></td><td></td></tr>
        <tr><td></td><td>Surgery</td><td></td><td></td><td></td><td></td></tr>
        <tr><td colspan='2'>Age</td><td></td><td></td><td></td><td></td></tr>
        <tr><td></td><td>[30,60)</td><td></td><td></td><td></td><td></td></tr>
        <tr><td></td><td>[60,100)</td><td></td><td></td><td></td><td></td></tr>
        <tr><td></td><td><30</td><td></td><td></td><td></td><td></td></tr>
        <tr><td colspan='2'>Diagnosis (primary)</td><td></td><td></td><td></td><td></td></tr>
        <tr><td></td><td>Diabetes</td><td></td><td></td><td></td><td></td></tr>
        <tr><td></td><td>Circulatory</td><td></td><td></td><td></td><td></td></tr>
        <tr><td></td><td>Digestive</td><td></td><td></td><td></td><td></td></tr>
        <tr><td></td><td>Genitourinary</td><td></td><td></td><td></td><td></td></tr>
        <tr><td></td><td>Injury</td><td></td><td></td><td></td><td></td></tr>
        <tr><td></td><td>Musculoskeletal</td><td></td><td></td><td></td><td></td></tr>
        <tr><td></td><td>Neoplasms</td><td></td><td></td><td></td><td></td></tr>
        <tr><td></td><td>Other</td><td></td><td></td><td></td><td></td></tr>
        <tr><td></td><td>Respiratory</td><td></td><td></td><td></td><td></td></tr>
        <tr><td>Numeric</td><td>Mean</td><td>Median</td><td>Std dev</td><td></td><td></td></tr>
        <tr><td>Time in Hospital</td><td></td><td></td><td></td><td></td><td></td></tr>
    
    </tbody>
</table>

## Modeling 30%
* Give a summary of the tool that you used for modeling – i.e., briefly describe DataRobot, including its mission.
* You should use three different “feature lists:” **Document which features you put into each list!!!! **
    * For your first one, use a small subsample of features that you would like to use as a “baseline” -- a simple model using attributes readily-collectible by a hospital that your better model should ideally outperform
    * For your second feature list, use a big feature list -- all of the features used by the authors in the paper. 
        * Kind of a “kitchen sink” approach. Throw in everything that you have selected for your list (i.e., every feature from the stats table above)
    * For your third feature list, select the “most informative features” from your best-performing model from the second approach. 
        * Ideally, the best model from a “most informative features” list will perform just as well or just marginally worse than the best-performing model from the kitchen-sink list. Remember, all else equal, parsimony is preferred.
        
* Using DataRobot, induce some models on your data. For each feature list:
    * One logistic regression model
    * One autopilot run reporting the top-performing model. Will probably be a “blended” model, assuming that autopilot actually ran a blender, but who knows with DataRobot amiright
    
Combining feature lists with modeling approaches, you can do the following...

||Logistic Regression|Best Autopilot Model|
|-|-|-|
|Feature list -- simple baseline|Model 1|Model 2|
|Feature list -- all|Model 3|Model 4|
|Feature list -- most informative from "all"|Model 5|Model 6|

_**No evaluation metrics in this table!!!**_

E.g., “we ran a logistic regression against three different feature lists. We also ran DataRobot’s “autopilot” feature for each feature list, which resulted in the following three models being selected as the ‘best-performing’ model for that list -- [model 1 with fancy name, model 2.... ]”

“Logistic regression works like this...

“The first autopilot one, model x, works like this...”

“The second autopilot one, model y, works like this...”
etc

* Describe briefly how logistic regression works, and also how your deploy-recommended DataRobot model works.
    * Note that DataRobot includes some very complicated-and-impressive-sounding models. However, with a bit of googling, you should be able to grasp how they work on a high level – enough to be able to describe to upper management how they work, anyway. In-depth knowledge of their workings is not necessary, but do your best to understand and describe them.

## Evaluation 30%

* Describe the DataRobot data partitioning and validation procedure that your models were trained on -- Indicate whether you used k-fold cross-validation or TVH. Indicate to management how this affords assessing the generalizability of your models.

### Reporting performance of all models:
*   What evaluation metric did you use? Describe it. Is higher or lower better etc, loosely how is it measured.
*   Report a summary table, using a table structure like I put up in the “modeling” section. E.g.,

    ||Logistic Regression|Best autopilot Model|
    |Feature List -- simple baseline|Performance of Model 1|Performance of Model 2|
    |Feature list -- all|Performance of Model 3|Performance of Model 4|
    |Feature list -- most informative from "all"|Performance of Model 5|Performance of Model 6|
    
* Speed-vs-accuracy of your selected models? Do you think that speed is important for this context?

### A deeper interpretation dive into the model that you recommend for deployment

* **Feature Importance:** Which features were the most predictive? Display and interpret feature importance, partial dependence, and reason code figures.**
* **Feature Impact:** What “information” do you gain from looking at the feature impact for your selected model? What patterns on readmittance prediction do you observe?
* **Lift chart:** Within what bins does your model perform best? For bins in which it does not perform well, in which directions does it err?
* **Prediction Explanations:** For the highest and lowest probability predictions, which features were most impactful, and in which direction?
* **ROC Curve**
    * Report best F1-score and interpret for management
    * For confusion matrix with cutoff at best f1-score, report accuracy, TPR, FPR, etc
    * Which performance matrix do you think is most important for this context (is a FP or a FN more costly? Which metric do you think is most important to minimize? )
    
**Note** -- DataRobot provides “feature importance” and “model x-rays” descriptions for each model. Read about these in the documentation and in your textbook, but the gist is that:
* Feature Importance shows which features are most predictive relative to all other features in your model, with the “most” predictive being the reference point, at 100%.
* Dependence (available on the Model X-ray tab) shows, among other stats, the “partial dependence” of each feature. This measure roughly represents the “estimate weight” attributable to each feature at each bin shown in the figure. If the feature is categorical, then each bin is just a different category. If the feature is numeric, then the feature is binned. The more different the “partial dependence” is at different bins, the more important that feature is for predictions. I.e., partial dependencies all on a straight line across bins would indicate that that feature is not predictive of the target variable. The partial dependence accounts for the predictive power of that feature-bin accounting for the predictive power of all other features included in the model. In other words, it is the “above and beyond” importance of that feature-bin in that model. Partial dependence is significant because it allows us to interpret feature importance as we would weights for features in a linear model, even for features in models that are normally very difficult to interpret (i.e., ones that do not make linear predictions). Read more here: https://cran.r-project.org/web/packages/datarobot/vignettes/PartialDependence.html
* Also examine “Prediction Explanations” e.g., “reason codes”. Read about them here: https://cran.r-project.org/web/packages/datarobot/vignettes/ReasonCodeVignette.html


## Evaluation -- Prediction against Management Holdout

* Management will provide to you a dataset with a few rows for which they will ask you to make a prediction of readmittance. They already know the answer, but they are using this data as a higher-level “holdout” of sorts to see how well your model can perform.
* To make these predictions, you should retrain the model that you are recommending for deployment on all available training data that you have uploaded to DataRobot. The assumption is that your model will be able to make better predictions against unseen data if it has been fed more training data.
* Once you have trained your recommended-deploy model on the full training dataset, use that model to make predictions for the data that management provides. Submit a file with your predictions in your final deliverable.
    * You only need to submit a csv with two columns:
    * The encounter id
    * Your prediction for readmittance within 30 days
* Management Holdout dataset available here: https://www.dropbox.com/s/guq79sp947cae6f/diabetic_data_management_holdout.csv?dl=0 


## Conclusion 

* High-level summary of your findings and recommendation


## Appendix – Feature Engineering and Restructuring

* Include an appendix with enough in-depth detail about all of your feature engineering and data restructuring that a programming team could start from raw data in the format that you received it, and modify it sufficiently that it could be used for modeling / predictions.
* Alteryx workflow:
    * Provide an alteryx workflow starting from the original data and ending with what you uploaded to DataRobot
* DataRobot screenshot: 
    * If you did any feature engineering or variable type specifications in DataRobot (e.g., type transformations), specify it here. Again, mention everything that a programming team would need in order to implement and deploy your model. Assume though that they are competent and don’t need hand-holding to carry out your steps. I.e., saying “join table x onto table y by columns (a,b,c)” and “extract ____ from feature ___; code as categorical” is sufficient, you don’t need to tell them click-by-click how to use any tool.

