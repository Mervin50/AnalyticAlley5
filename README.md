## Project Name : Salary Prediction and Analysis

![salary image](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/1679ab76-cd56-449a-b2e1-4bce434b304b)

# Table of contents

1. Introduction
   
2. Description of the dataset
   
   2.1. Intial steps:

   2.2. Descriptive statistics

4. Exploratory Data Analysis

   3.1 Bar plot for visualization of top 10 Grade Category distribution

   3.2 Bar chart for distribution of gender in percentage

   3.3 Barplot for Top 10 divisions

   3.4 Distribution of Base salary

   3.5 Distribution of 2020 Longetivity pay

   3.6 Top 10 Departments based on average base salary

   3.7 Top 5 divisions based on 2020 overtime pay distribution

   3.8 Distribution of Base Salary based on Gender

   3.9 Heatmap of Top 10 Divisions vs Gender
   
6. Data Cleaning

   4.1 Outlier Detection and Treatment

       4.1.1 Z-score Method

       4.1.2 Winsorizing Technique

       4.1.3 Implementation

       4.1.4 Winsorizing explanation of code

8. Data Splitting and Preprocessing

9. Model Selection and Evaluation

   6.1 MSE

       6.1.1 MSE model performance

       6.1.2 MSE model accuracy evaluation

   6.2 R^2 score

       6.2.1 R^2 scores of all 3 models

       6.2.2 R^2 score evualation

   6.3 Precision, Recall and F1-score

       6.3.1 Precision explanation

       6.3.2 Recall explanation

       6.3.3 F1-score explanation

       6.3.4 F1, Precision and Recall score of Linear Regression

       6.3.5 F1, Precision and Recall score of Random Forest

       6.3.6 F1, Precision and Recall score of SVM

    6.4 Confusion Matrix

       6.4.1 Confusion Matrix of Random Forest and SVM

7. Conclusion

18. References
   
   
      
          
# 1. Introduction:
This README describes work done on the "Employee Compensation and Satisfaction Insights" Dataset. Resources used include Python and associated packages Google Colab, matplotlib, Seaborn, scikit-learn, statsmodels, and SciPy. We have addressed the regression challenge to uncover the factors impacting salaries, employing Support Vector Machine, Random Forest, and Linear Regression.

# 2. Description of the dataset:

##### 2.1 Initial steps:
The very first step is always to check if the data needs cleaning by looking for duplicate rows, zero values or NaNs where they shouldn't be etc. The head of the data set looks like:
![head of our dataset](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/d8afebcf-29bb-4c87-a01e-abb075c2a22a)

##### 2.2 Descriptive statistics:
Pandas describe() can provide a quick summary of the dataset as outlined in the notebook. The output of pandas describe() is shown below. Here, all columns of the DataFrame are included in the analysis.

![describe function](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/c551c3f9-b161-4251-9af4-4b16656075e7)

From this summary we can say that:

A) Base Salary:
The average base salary is approximately $78,771.
The minimum base salary is $11,147, while the maximum is $280,000.
The distribution of base salaries appears to be right-skewed, as the mean is higher than the median (50th percentile).

B) 2020 Overtime Pay:
The average overtime pay for 2020 is around $5,182.
Overtime pay varies widely, with a standard deviation of approximately $11,063.
The maximum overtime pay received in 2020 is notably high at $141,998.

C) 2020 Longevity Pay:
On average, employees received around $924 in longevity pay for the year 2020.
Similar to overtime pay, longevity pay also varies considerably, with a standard deviation of approximately $2,044.
A large portion of employees (75th percentile) did not receive any longevity pay in 2020.

# 3. Exploratory Data Analysis:

##### 3.1 Exploratory Analysis of Organizational Structure and Workforce Diversity

![Screenshot 2024-05-03 100650](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/1d530789-0936-44a0-a2c5-483383c32d0a)

A) Grade 15 is the most common, occurring 1125 times, followed by grade 20 with 314 occurrences.

B) The 'grade' column categorizes employees by roles or positions, while 'gender' shows their distribution.

C) Insights into gender distribution aid in workforce diversity strategies and organizational decision-making.

##### 3.2 Comprehensive Analysis of Compensation and Departmental Performance

![1p](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/16e0076a-8115-4204-9a17-377a7f757683)
![2p](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/6c616111-cd8d-4256-bf92-c9d328a66b63)

A) Over 5000 employees earn $100,000, with the fewest earning $250,000. 

B) Approximately 8000 employees do not receive overtime pay, while around 1000 receive $1000. 

C) For longevity pay, around 8000 employees receive nothing, 250 receive $2000, and another 250 receive $8000.

D) Department 1 has an average salary of $140,000, while Department 10's average salary is approximately $120,000, suggesting differences in compensation across 
   departments.


##### 3.3 Distribution of Base Salary based on Gender.

![Distribution of Base Salary by Gender](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/7fbfbc96-daa4-4edd-b663-5b8061b69878)

Overall, the kernel density plots offer a visual tool for comparing the distribution of base salaries by gender, allowing for insights into potential patterns, discrepancies, or commonalities in salary structures.

##### 3.4 Heatmap of Top 10 Divisions vs Gender

![Heatmap](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/6b0aa1aa-c74c-4ade-9bec-2a0339ccc429)

Overall, the heatmap provides a clear and concise overview of the gender distribution within the top divisions, offering insights into potential areas for further analysis or targeted HR interventions.

# 4. Data Cleaning: 

##### 4.1 Outlier Detection and Treatment:
Upon visual inspection of our box plot, we observed the presence of outliers within our dataset. To address this, we implemented a robust outlier detection and treatment approach using Z-score.

##### 4.1.1 Z-score Method:
The Z-score method is a statistical technique used to identify outliers by measuring how many standard deviations an observation is from the mean. Observations with a Z-score greater than a specified threshold are flagged as outliers.

##### 4.1.2 Winsorizing Technique:
To handle the identified outliers, we applied the winsorizing technique. Winsorizing involves capping extreme values by replacing them with less extreme values. Specifically, we set the lower cap at the 5th percentile and the upper cap at the 95th percentile of the data distribution.

##### 4.1.3 Implementation:
Outlier Detection: We calculated the Z-scores for each data point.

##### 4.1.4 Winsorizing: Data points below the 5th percentile were adjusted to the value at the 5th percentile, while those above the 95th percentile were adjusted to the value at the 95th percentile.
By applying the winsorizing technique, we effectively mitigated the impact of outliers on our dataset, ensuring robustness and reliability in our analysis.

##### 5. Data Splitting and Preprocessing:

In this step, we split our dataset into features and the target variable. Our target variable, base salary (y), is separated from the features (X). We then utilize a ColumnTransformer for preprocessing, which allows us to apply various transformations selectively to different columns in our data. We've employed a OneHotEncoder within this transformer to encode categorical data. This preprocessing pipeline is specifically tailored to one-hot encode the categorical columns while leaving the non-categorical columns unchanged.

# 6. Model Selection and Evaluation (MSE): 

### 6.1 MSE:

##### 6.1.1 MSE model performance:

We've explored the performance of three different models: Support Vector Machine (SVM), Linear Regression, and Random Forest Regression. To evaluate these models, we've utilized the Mean Squared Error (MSE) metric. MSE quantifies the average squared difference between the actual and predicted values. A lower MSE indicates better model performance, signifying that the model's predictions are closer to the actual values.

![MSE](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/60c2d904-0db1-4828-b849-a22ffbf8256c)


##### 6.1.2 MSE model accuracy evaluation:

a) Linear Regression MSE: 94727842.27752575

b) Random Forest Regressor MSE: 88475403.21661408

c) Support Vector Regressor MSE: 699046712.7006655

We can make the following observations about the accuracy of the models:
The Random Forest Regressor has the lowest MSE among the three models, indicating that it provides the most accurate predictions among them. The Linear Regression model has a higher MSE than the Random Forest model but lower than the Support Vector Regressor, suggesting that it performs moderately well in terms of accuracy. The Support Vector Regressor has the highest MSE, indicating that it provides the least accurate predictions among the three models.

### 6.2 R^2 score:

##### 6.2.1 R^2 scores for all three models:

![R2 score](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/5629722a-3d52-471f-8313-dbd947d5ed94)

We have also found R2 scores of all three models: 
The R^2 scores indicate how well the regression models fit the data:
Linear Regression R^2 Score: 0.8643
Random Forest Regression R^2 Score: 0.8732
Support Vector Regression (SVR) R^2 Score: -0.0015

##### 6.2.2  R^2 score evaluation:

A score of 1 indicates a perfect fit.
A score of 0 indicates that the model performs no better than simply taking the mean of the target variable.
Negative scores indicate that the model performs worse than a horizontal line.

Given these scores:

Both Linear Regression and Random Forest Regression models have decent R^2 scores, indicating a good fit to the data.The Support Vector Regression (SVR) model has a negative R^2 score, which suggests that it performs worse than a horizontal line. This could mean that the SVR model is not suitable for this dataset or may require further tuning. In summary, the Linear Regression and Random Forest Regression models seem to provide reasonable fits to the data, while the SVR model may need further investigation or alternative approaches.

### 6.3 Precision, Recall and F1-score:

##### 6.3.1 Precision:

Precision measures the accuracy of the positive predictions made by the model. It is the ratio of correctly predicted positive observations to the total predicted positives.

Precision = TP / (TP + FP)

TP (True Positives): The number of correctly predicted positive instances.
FP (False Positives): The number of incorrectly predicted positive instances.
Recall (also known as sensitivity or true positive rate):

##### 6.3.2 Recall: 

Recall measures the ability of the model to find all the positive instances. It is the ratio of correctly predicted positive observations to the all actual positives in the dataset.

Recall = TP / (TP + FN)
FN (False Negatives): The number of incorrectly predicted negative instances.


##### 6.3.3 F1-score:

F1-score is the harmonic mean of precision and recall. It provides a balance between precision and recall. F1-score reaches its best value at 1 and worst at 0.

F1-score = 2 * (Precision * Recall) / (Precision + Recall)

These metrics are commonly used in classification tasks to evaluate the performance of a model. 

##### 6.3.4 F1, Precision and Recall score of Linear Regression: 

![LR1](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/d3cf1991-aae6-48d5-a989-76df2a2ff446)

##### 6.3.5 F1, Precision and Recall score of Random Forest:

![F1 for RF](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/1f6c3ce5-84bb-436f-9a4c-30c92c8d5197)

##### 6.3.6 F1, Precision and Recall score of SVM:

![F1 for SVM](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/dcbe0b97-8610-4ef4-b002-f29507c7185d)

The Random Forest Regression model shows the best performance with higher precision, recall, and F1-score compared to Linear Regression and SVR. The Support Vector Regression model (SVR) has notably lower precision, recall, and F1-score, indicating poorer performance compared to the other models. This may suggest that the SVR model is not well-suited for the given task or requires further optimization.

# 6.4 Confusion Matrix: 

A confusion matrix is a table that is often used to describe the performance of a classification model on a set of test data for which the true values are known. It allows visualization of the performance of an algorithm by showing the number of correct and incorrect predictions in each class.

Here's how a confusion matrix is typically structured for a binary classification problem:


![confusion matrix](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/8a952897-82ee-4722-81f6-0a8269c646fe)

The confusion matrix is specifically designed for classification tasks where we predict discrete classes. For regression tasks, where we are predicting continuous values like salaries, the confusion matrix doesn't apply.



# 7. Conclusion:
The classifiers, including Random Forest, Decision Tree, and Support Vector Machine, demonstrated varying levels of accuracy, with Random Forest exhibiting the highest predictive capability. The project not only achieved its primary objective of creating a salary prediction model but also laid the groundwork for future refinements. Further enhancements may involve optimizing hyperparameters, exploring alternative algorithms, and incorporating additional features to boost model accuracy. Overall, our data-driven approach and machine learning solutions have contributed to informed decision-making regarding salary structures, potential pay disparities, and budget planning within the organization.


# 8. References:
General:

[1] Anaconda Distribution https://www.anaconda.com/

[2] Python Software Foundation https://www.python.org/

[3] seaborn: statistical data visualization https://seaborn.pydata.org/index.html#

[4] matplotlib: Python plotting library https://matplotlib.org/

[5] "Employee Compensation and Satisfaction Insights" Dataset from data.world [https://github.com/mwaskom/seaborn-data/blob/master/tips.csv](https://data.world/montgomery-county-of-maryland/1fc1fc94-d685-4c4f-9525-6e6079165315/workspace/file?filename=comma-separated-values-file-1.csv)

[6] scikit-learn: Machine Learning in Python https://scikit-learn.org/stable/index.html

[7] statsmodels: Statistics in Python https://www.statsmodels.org/stable/index.html

[8] scipy.stats : Statistics with SciPy https://docs.scipy.org/doc/scipy/reference/tutorial/stats.html

Exploratory data analysis:

[9] Exploratory Statistical Data Analysis with a Real data set using Pandas https://towardsdatascience.com/exploratory-statistical-data-analysis-with-a-real-data set-using-pandas-208007798b92

[10] How to investigate a data set with Python https://towardsdatascience.com/hitchhikers-guide-to-exploratory-data-analysis-6e8d896d3f7e

[11] Data analysis with Python https://medium.com/@onpillow/01-investigate-tmdb-movie-data set-python-data-analysis-project-part-1-data-wrangling-3d2b55ea7714

[12] Python for Data Analysis: Data Wrangling with Pandas, NumPy, and IPython. Wes McKinney. ISBN-13: 978-1491957660 ISBN-10: 1491957662

[13] Pandas In 10 Minutes || Wes McKinney https://www.youtube.com/watch?v=1MGCD8SQp3k

[14] Good description of quartiles on Seaborn plots https://towardsdatascience.com/analyze-the-data-through-data-visualization-using-seaborn-255e1cd3948e

Regression:

[15] Ordinary Least Squares in statsmodels https://www.statsmodels.org/dev/examples/notebooks/generated/ols.html

[16] Generalized Linear Models in scikit-learn https://scikit-learn.org/stable/modules/linear_model.html#ordinary-least-squares

[17] How to run Linear regression in Python scikit-Learn https://bigdata-madesimple.com/how-to-run-linear-regression-in-python-scikit-learn/

[18] A beginner’s guide to Linear Regression in Python with Scikit-Learn https://towardsdatascience.com/a-beginners-guide-to-linear-regression-in-python-with-scikit-learn-83a8f7ae2b4f

[19] Regression Analysis: How Do I Interpret R-squared and Assess the Goodness-of-Fit? https://blog.minitab.com/blog/adventures-in-statistics-2/regression-analysis-how-do-i-interpret-r-squared-and-assess-the-goodness-of-fit

[20] Python and R Tips To Learn Data Science: Pearson and Spearman Correlation in Python https://cmdlinetips.com/2019/08/how-to-compute-pearson-and-spearman-correlation-in-python/




