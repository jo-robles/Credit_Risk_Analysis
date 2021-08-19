# Credit Risk Analysis
 
## Overview
Utilizing data from credit cards from LendingClub issued out in Quarter 1 of 2019, we utilize supervised machine learning to make predictions on credit risk. We utilize the following 6 machine learning models to accomplish this:

* RandomOverSampler
* SMOTE
* ClusterCentoids
* SMOTEEN
* BalancedRandomForestClassifier
* EasyEnsembleClassifier

After the results have been compiled, we evaluate and make a recommendation on their utilization towards predicting  credit risk. 
## Results
Once the source file CSV has been cleaned, the first step of our machine learning process is to determine our X and y variables. In our case, the y (dependent variable) is defined as the loan status of the account with the X (independent variable) is defined as every other column.

* RandomOverSampler
	* Utilizing the following code ```from sklearn.metrics import balanced_accuracy_score```, we calculate our balanced accuracy score: 

		![Balanced ROS](https://github.com/jo-robles/Credit_Risk_Analysis/blob/253acea69e6ca579c73f84e90e5e67d67bb53736/Resources/ros_balance.PNG)
	
		As a review, accuracy is simply defined as the percentage of correct predictions. The balanced accuracy score (noted here) is the average accuracy per class. In our case, we see that the balanced accuracy score for  RandomOverSampler is 66%
	* To find our precision and recall scores, we can either calculate these from the confusion matrix (e.g., Precision = TP/(TP+FP) or we can import the classification report when we also import our confusion matrix in our dependencies. For sake of ease (and consistency), we will be utilizing the classification report by executing the following code: ```from imblearn.metrics import classification_report_imbalanced```. After which, we observe the following:

		![Balanced Scores](https://github.com/jo-robles/Credit_Risk_Analysis/blob/253acea69e6ca579c73f84e90e5e67d67bb53736/Resources/ros_scores.PNG)

		In our example here, we note that the precision is extremely high for low_risk credit but extremely low for high_risk credit. For our recall values, we see that for both high and low risk, that value is about 66% for either one. For context, this means that within our model, the number of positive predictions that were correct are about the same for either high or low risk. 

* SMOTE
	* Utilizing the same method as before, we calculated our balanced accuracy score:
		
		![Smote Balance](https://github.com/jo-robles/Credit_Risk_Analysis/blob/253acea69e6ca579c73f84e90e5e67d67bb53736/Resources/smote_balance.PNG)
		
		As noted above, the value here is 63% for our current model. 
		
	* Additionally, utilizing the same method as before, we find the following:

		![Smote Scores](https://github.com/jo-robles/Credit_Risk_Analysis/blob/253acea69e6ca579c73f84e90e5e67d67bb53736/Resources/smote_scores.PNG)

		Of note is that our precision score is the exact same as it was with our RandomOverSampler (extremely high for low risk and extremely low for high risk). Our recall score, we see similar values for both our low and high risk (64% and 62% respectively). 
		
* ClusterCentoids
	* Next, we utilizing an under-sampling model and calculate our balanced accuracy score:

		![CC Balance](https://github.com/jo-robles/Credit_Risk_Analysis/blob/253acea69e6ca579c73f84e90e5e67d67bb53736/Resources/cluster_balance.PNG)

		We note then that the change in approach has changed our accuracy score to 51%.

	* And, as before, we utilize the imbalanced classification report to find our precision and recall scores:

		![CC Scores](https://github.com/jo-robles/Credit_Risk_Analysis/blob/253acea69e6ca579c73f84e90e5e67d67bb53736/Resources/cluster_scores.PNG)

		We note that our precision scores have not changed between our previous oversampling models but that our recall values have changed quite a bit. Instead of being in the 60s, we now observe much lower values. And, in fact, we note that the recall value for high risk is finally higher than low risk (59% vs 43%).

* SMOTEEN
	* Next, we use a combination of over and under-sampling. We begin by taking a look at our balanced accuracy score:

		![Smote Balance](https://github.com/jo-robles/Credit_Risk_Analysis/blob/253acea69e6ca579c73f84e90e5e67d67bb53736/Resources/smote_balance.PNG)
	
		As noted, we are reporting at 66%.

	* And, as before, we utilize the imbalanced classification report to find out precision and recall scores:

		![Smote Score](https://github.com/jo-robles/Credit_Risk_Analysis/blob/253acea69e6ca579c73f84e90e5e67d67bb53736/Resources/smote_scores.PNG)

		We note our precision scores are the same but (as with under-sampling), the recall score for high risk is much higher (74% vs 58%).
		
* BalancedRandomForestClassifier
	* As expected, we calculate our balanced accuracy score:

		![Forest Balance](https://github.com/jo-robles/Credit_Risk_Analysis/blob/253acea69e6ca579c73f84e90e5e67d67bb53736/Resources/forest_balance.PNG)

		We see that with this model we report our accuracy score as 79%. 

	* And, as before, we utilize the imbalanced classification report to find out precision and recall scores:

		![Forest Score](https://github.com/jo-robles/Credit_Risk_Analysis/blob/253acea69e6ca579c73f84e90e5e67d67bb53736/Resources/forest_scores.PNG)

		We finally see a slightly higher precision score for our high risk but a much larger recall for lower risk as compared to high risk. 

* EasyEnsembleClassifier
	* Finally, we calculate our last balanced accuracy score:

		![Easy Balance](https://github.com/jo-robles/Credit_Risk_Analysis/blob/253acea69e6ca579c73f84e90e5e67d67bb53736/Resources/easy_balance.PNG)

		We see that with this model we report our accuracy score as - 93%. 

	* And, as before, we utilize the imbalanced classification report to find out precision and recall scores:

		![Easy Scores](https://github.com/jo-robles/Credit_Risk_Analysis/blob/253acea69e6ca579c73f84e90e5e67d67bb53736/Resources/easy_scores.PNG)

		We see that our high risk precision score is the highest so far and that our recall as well is reported as high for both high and low risk. 

## Summary
In summary, we observe that each of the models present slightly different results in attempting to determine those that may be high risk. In certain situations, our models are extremely efficient at finding low risk but not very good at high. With that in mind, it appears as though our last model (EEC) gives us at least a baseline of what we can utilize. This is taken into consideration of the recall value for both. While the precision leaves a bit to be desired, it is the best model we have at this moment. 