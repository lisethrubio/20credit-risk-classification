# 20credit-risk-classification

## Overview of the Analysis 


Historical lending activity is crucial for identifying the creditworthiness of borrowers, as it provides insight into their past financial behavior and ability to manage debt. Key factors include the size of the loan, with larger loans needing a closer look at whether the borrower can pay it back; the interest rate, which is the cost of borrowing and is usually lower for those with good credit; and the borrower’s income, which shows their ability to make payments. The debt-to-income ratio is important because it shows how much of their income goes to paying off debt. The number of credit accounts they have can also show their experience with managing credit. Negative marks like late payments or bankruptcies can be a big warning sign, and the total amount of debt they owe can indicate whether they might struggle to pay back a new loan. All these factors together help lenders decide whether someone is a good candidate for a loan.
By utilizing logistic regression models, this supervised machine learning classification application can predict the likelihood of a borrower repaying a loan based on their historical data. The accuracy and reliability of the model, as assessed by the evaluation metrics, provide confidence that decisions made using this model are based on solid data and analysis, thereby reducing the risk of lending to someone who might default on the loan. This analysis in divided in three sections: 

### **Part 1:** Importing Dependencies
This section outlines the necessary dependencies for the project. The *`NumPy`* library is employed for numerical computing in Python, offering support for multi-dimensional arrays and a variety of mathematical functions. The *`Pandas`* library is utilized for data manipulation and analysis, particularly for handling structured data using DataFrames. *`Pathlib`* is imported to simplify file path management through an object-oriented approach. For machine learning purposes, *`Scikit-learn’s train_test_split`* is imported to divide datasets into training and testing subsets, facilitating model validation. Additionally, *`Scikit-learn’s confusion_matrix`* and *`classification_report`* are utilized to provide detailed metrics and evaluate the performance of classification, logistic regression model.

### **Part 2:** Splitting Data into Training and Testing Sets
In this section, the independent (features) and dependent variables (labels) from the DataFrame are separated to prepare them for splitting into training and testing sets. Initially, the *`“lending_data.csv”`* file from the *`“Credit-Risk”`* folder is loaded into a Pandas DataFrame named *`"lending_data_df"`*, which contains 8 columns and 77,536 rows of data. The label set *`y`* represents the target variable that the model aims to predict, specifically the *`"loan_status"`* column, which serves as the dependent variable (output data or labels). The features *`X`* consist of the independent variables (input data) that the model will use to make predictions. After separating these columns, the data is split into training and testing sets using the *`train_test_split`* function. By default, 75% of the data is allocated for training and 25% for testing.

During the training and evaluation phases, four variables are created: *`"X_train"`* and *`"y_train"`* are training subsets of *`X`* and *`y`* that will be used to train the model, while *`"X_test"`* and *`"y_test"`*, are the training subsets of *`X`* and *`y`* reserved for evaluating the model's performance on unseen data. The *`shape()`* attribute in Python is then used to provide the dimensions of the *`"X_train"`* training set, indicating the number of rows (samples) and columns (features) present in the training set.

### **Part 3:** Creating a Logistic Regression Model with the Original Data
In this section, the logistic regression model is trained using the training data set (*`"X_train"`* and *`"y_train"`*). This model is then used to make predictions that will be compared to the actual labels to assess performance. Initially, the *`LogisticRegression`* class is instantiated to create the logistic regression model. The *`solver='lbfgs'`* argument specifies the *`lbfgs`* algorithm, which is suitable for smaller datasets, and defines the optimization method for fitting the model. The *`max_iter=200`* parameter sets the maximum number of iterations for the algorithm, while *`random_state=1`* ensures reproducibility. The *`fit()`* method is employed to train the logistic regression model using the training data. Subsequently, the *`predict()`* method generates predictions based on the input data, with the results stored in the *`"predictions"`* variable. A new DataFrame, named *`"predictions_results"`*, is created to display the predictions alongside the actual labels.

To evaluate the performance of the logistic regression model, the *`confusion_matrix`* function is used to compute a confusion matrix, comparing the actual labels (*`"y_test"`* subset) with the predicted labels (*`"predictions"`* variable). The matrix reveals how many instances of each class were correctly predicted versus how many were misclassified. Finally, a classification report is generated to present key metrics, including precision, recall, F1-score, and support, which are specific to each class. The report also provides an accuracy metric, which represents the ratio of correctly predicted instances (true positives and true negatives) to the total number of instances across all classes. This metric offers a general measure of the model's overall performance rather than its effectiveness with respect to any specific class.



## Results

Among the 18,746 instances actually labeled as *`“healthy loans”`*, 18,679 were correctly predicted, while 67 were incorrectly predicted and misclassified as high-risk when they were actually *`“healthy loans”`*. This means that *`99.6%`* of the actual healthy loans were accurately predicted, with only *`0.4%`* incorrectly predicted and misclassified as *`"high-risk loans"`*. On the other hand, of the 638 instances actually labeled as *`“high-risk loans”`*, 558 were correctly predicted, while 80 were incorrectly predicted and misclassified as healthy when they were actually *`“high-risk loans”`*. This translates to an *`87.5%`* accuracy rate for predicting high-risk loans, with *`12.5%`* of these predictions being incorrect and misclassified.

The classification report shows that the model performs exceptionally well in predicting "Healthy Loans," achieving perfect scores with a precision, recall, and F1-score of 1.00. For "High-Risk Loans," the model has a precision of 0.87, meaning 87% of the loans predicted as high-risk are actually high-risk. It has a recall of 0.89, indicating it correctly identifies 89% of all actual high-risk loans. The F1-score, which balances precision and recall, is 0.88 for high-risk loans, showing good but not perfect performance. Overall, the model has an accuracy of 99%, meaning it correctly classifies 99% of all 19,384 loans. The macro average, which averages the precision, recall, and F1-score across both loan types equally, is 0.94 for each metric. The weighted average, which takes into account the larger number of healthy loans, is 0.99 for precision, recall, and F1-score. While the model is highly accurate overall, its performance on identifying high-risk loans could be further improved, as this is where most of the errors occur.


## Summary 

The evaluated machine learning model exhibits outstanding performance in predicting *`"Healthy Loans"`*, achieving perfect scores with a precision, recall, and F1-score of 1.00, correctly classifying 99.6% of actual healthy loans. In contrast, the model performs adequately but not flawlessly in identifying *`"High-Risk Loans"`*, with a precision of 0.87, recall of 0.89, and F1-score of 0.88, leading to 12.5% of high-risk loans being misclassified as healthy. The overall accuracy across all loan types stands at 99%, with macro and weighted averages reflecting the dominance of *`"Healthy Loans"`* in the dataset. While the model's general performance is strong, the misclassification rate of *`"High-Risk Loans"`* presents a significant concern when the primary objective is accurately identifying high-risk borrowers.

If the main goal is to identify *`"high-risk borrowers"`*, the model's current performance is good but not perfect and it needs improvement in this area, even though it performs well overall. The most critical issue is the misclassification of high-risk loans as healthy, which could lead to potential financial risks. Improving the model’s recall and precision for high-risk loans should be prioritized to reduce the number of false negatives (high-risk loans incorrectly classified as healthy).
<br> To better identify *`"high-risk borrowers"`*, it would be helpful and recommended to improve the model or try different methods to reduce the number of high-risk loans that are misclassified. Adjusting the classification threshold, using a different model, or applying cost-sensitive learning could increase the accuracy of high-risk loan predictions. 
In summary, while the model performs well, its ability to correctly identify high-risk borrowers is the most important metric in this context. Enhancements should be made to reduce errors in predicting high-risk loans to ensure more reliable decision-making.

## Summary Bullet Points 

- Outstanding Performance in "Healthy Loans" Prediction:

    - Precision, Recall, and F1-Score: 1.00 (Perfect Scores)
    - Correct Classification Rate: 99.6% for actual healthy loans

- Adequate but Not Flawless in "High-Risk Loans" Identification:

    - Precision: 0.87
    - Recall: 0.89
    - F1-Score: 0.88
    - Misclassification Rate: 12.5% of high-risk loans misclassified as healthy

- Overall Model Accuracy:

    - Accuracy: 99%
    - Macro and Weighted Averages: Reflect the dominance of "Healthy Loans" in the dataset

- Critical Concern:

    - High-Risk Loans Misclassification: Significant concern due to potential financial risks
    - Main Objective: Accurate identification of high-risk borrowers
- Model Improvement Recommendations:

    - Enhance Recall and Precision for High-Risk Loans to reduce false negatives
    - Consider Adjusting the Classification Threshold, Using a Different Model, or Applying Cost-Sensitive Learning

- Summary:

    - Model performs well overall, but improving high-risk loan identification is critical for reliable decision-making.

