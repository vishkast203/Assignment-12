# Assignment-12
Assignment-12: Supervised Learning
Executove Summary: The project team was tasked with building a model that could identify the creditworthiness of borrowers by analyzing a dataset of historical lending activity from a peer-to-peer lending services company. The code for this project was successfully created and validated. Two versions of the dataset were compared and the code proved it's ability to learn from the original data set and predict performace using test data. Therefore new data can be tested to forecast future creditworthiness of borrowers.

Analytical Tools and Libraries
The following modules & libraries were used:  Python version 3.8, numpy, pandas, pathlib, sklearn (balanced_accuracy_score, confusion_matrix) & imblearn (classification_report_imbalanced). 

Analytical Steps: 
The code was created using our knowledge of the imbalanced-learn library, with a logistic regression model to compare two versions of the dataset. First, we used the original dataset. Second,we resampled the data by using the RandomOverSampler module from the imbalanced-learn library.

For both cases, we got the count of the target classes, trained a logistic regression classifier, calculated the balanced accuracy score, generated a confusion matrix, and finally generated a classification report. 

Once the required modules were imported, the first step was to read the csv file provided where the loan_status column was identified as containing the count of the target classes. This was labelled as the 'y' feature & the rest of the dataframe was was the X feature (using the dropna() function). 
Once the data was separated into X & y, the data was split into testing and training sets using the [X_train, X_test, y_train, y_test = train_test_split(X, y)].  At this point we checked the count of the healthy & high-risk loasns in the loan_status column (healthy = 75036; high-risk = 2500). This reflected the inherent imbalance in the data which should be anticipated as healthy loans would typically easily outnumber risky loans.


The logistic regression classifier was initated and used to fit the the training data set followed by importing the LogisticRegression module from SKLearn
(from sklearn.linear_model import LogisticRegression). The model was instantiated assigning a random_state parameter of 1 to the model. The model was then fit to the training dataset. 

Next the outputs were obtained (Balanced Accuracy Score, Confusion Matrix & Classification reprot) for the original data. The following resuts were seen:
                pre       rec       spe        f1       geo       iba       sup

          0       1.00      0.99      0.91      1.00      0.95      0.91     18765
          1       0.85      0.91      0.99      0.88      0.95      0.90       619

    avg / total    0.99      0.99      0.91      0.99      0.95      0.91     19384

The classification  report summarizes the data analysis for the original data set for (0)) 'healthy loans' & (1) high-risk loans'. The precision and the recall for the 0 class  is much better than that for the 1 class. The Precision for the 0  class, 99%  of the time the predictions were correct versus 85% of the time for the high-risk loan class which also causes a lower F1 score (which uses the calculated Precision & Recall values) for the 'high-risk loan'. In summary the model performance is as expected not a perfect fit on the test data set which is to be expected as the model is using the test data for the first time. It is a good comparison for future performance of the model on new real world data sets.  

The same process was repeated but using the RandomOverSampler module from imbalanced-learn. We then fit the original training data to the random_oversampler model. A count of the distinct values of the resampled labels data reflected the following: (0= 56271; 1 = 56271) which showed that the random oversampling of the smaller dataset had been performed. Next the final outputs were generated fo the test data:
      pre       rec       spe        f1       geo       iba       sup

          0       1.00      0.99      0.99      1.00      0.99      0.99     18765
          1       0.84      0.99      0.99      0.91      0.99      0.99       619

    avg / total   0.99      0.99      0.99      0.99      0.99      0.99     19384

    The logistic regression model fits with the oversampled data very well with a very low count of False Negatives. One key measure that indicates a strong fit is the Recall (Sensitivity) value for the Test dataset that shows 99% accuracy (TP/TP+FN) while the confidence measure (Precision) stayed nearly the same between the original data set & the oversamped data (0.84 vs. 0.85). The Recall value went up to 99% (vs. 91% on the original data set) which shows that the higer the number of samples tested,  the more accurate the model output. In summary for the healthy loans,  there was hardly any improvement (as there was no real room for improvement ) &  the high-risk data prediction improved.