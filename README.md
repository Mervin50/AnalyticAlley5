# AnalyticAlley

# 1. Introduction:
This README describes work done on the "Employee Compensation and Satisfaction Insights" Dataset. Resources used include Python and associated packages Google Colab, matplotlib, Seaborn, scikit-learn, statsmodels, and SciPy. The analysis takes the form of a single Google Colab notebook of filename given above. To view this file, download it from this repository. All images intended for inclusion in this README are located in the images subdirectory of this repository. I have tried to structure the Google Colab notebook and this README so that they have corresponding sections. However, I do not wish to merely repeat here what has been stated in the notebook. I will endeavour to have this README summarize the work of the notebook and, hopefully, complement the analyses done there.

# 2. Description of the dataset:
Predictive analysis is a form of analytics that employs statistical and machine learning techniques to recognize patterns and forecast outcomes. By scrutinizing historical and current data, predictive data analysis identifies trends and behaviours, enabling proactive decision-making for the future. This proactive approach assists businesses in minimizing risks and seizing opportunities, ultimately enhancing the decision-making process. In the context of our dataset, which encompasses information about departmental attributes, employee demographics, and salary-related variables, our objective is to construct a model capable of predicting salaries across varius departments within an organization. This endeavour aims to streamline salary structures, pinpoint potential pay disparities, and contribute to effective budget planning. Additionally, machine learning models can provide valuable insights to the HR department regarding salary distribution and compensation fairness.

# 2.1 Initial steps:
I often use sites such as Medium.com to see how other people have investigated data sets using Python. The very first step is always to check if the data needs cleaning by looking for duplicate rows, zero values or NaNs where they shouldn't be etc. The head of the data set looks like:
![head of our dataset](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/d8afebcf-29bb-4c87-a01e-abb075c2a22a)

# 2.2 Descriptive statistics:
Pandas describe() can provide a quick summary of the data set as outlined in the notebook. So it seems like a sensible command to run. The output of pandas describe() is shown below. Here, all columns of the DataFrame are included in the analysis.
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

3.1 Bar plot for visualization of top 10 Grade Category distribution

![top 10 grade](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/4eef41ce-98cb-47b8-911c-2dccbe2512e0)

15: This grade occurs 1125 times and is the most frequently assigned grade in the dataset.        
20: This grade appears 314 times in the dataset. 
The 'grade' column in the dataset represents the classifications assigned to employees based on their roles or positions within the organization. Each unique grade signifies a specific level of responsibility, skill requirements, or seniority.

3.2 Bar Chart for distribution of gender in percentage

![Distribution of gender](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/2505ec42-d4bd-417c-92b5-215eb2ee7244)

The 'gender' column in the dataset indicates the distribution of employees based on their gender. In summary, the 'gender' distribution in the dataset suggests a higher representation of male employees compared to female employees. This information can be valuable for understanding the gender composition within the workforce and may be considered in various analyses or decision-making processes related to gender diversity and inclusion. Overall, gender distribution insights are valuable for organizations aiming to foster diversity and make data-driven decisions related to human resources and workforce management.

3.3 Barplot for Top 10 divisions

![Top 10 divisions](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/0db5cdde-cd36-4795-875c-9a99aee17dc0)

School Health Services has the highest count among the top 10 departments, indicating that it has a significant presence within the organization. 
Transit Gaithersburg Ride On and Transit Silver Spring Ride On are transit-related departments, suggesting that transportation services are substantial aspects of the organization's operations.
Office of Eligibility and Support Services is also prominently featured, indicating a focus on providing eligibility and support services, possibly related to social welfare or assistance programs.
Highway Services is another notable department, highlighting the organization's involvement in managing highways or road infrastructure.

3.4 Distribution of Base Salary

![Distribution of base salary](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/d4715573-f869-469d-81d0-f3c1a09fd571)

The histogram depicts the distribution of base salaries among employees in the dataset. Insights from the histogram suggest that the dataset primarily consists of employees with salaries in the lower to mid-range, with a substantial concentration of around $50,000. 
The distribution reveals a skewed pattern, indicating that a smaller proportion of employees receive higher salaries, with a peak of around $100,000. 
This information can be valuable for understanding the salary distribution within the organization and may guide decision-making related to compensation and budget planning.

3.5 Distribution of 2020 Longevity Pay

![Distribution of longevity of pay](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/0e1f5448-baab-4c81-9ea9-9188de526131)

These insights suggest that the majority of employees did not receive or received very less longevity pay in 2020, with a smaller percentage receiving varying amounts, as indicated by the specified bins in the displot.

3.6 Top 10 Departments based on Average Base Salary

![Top 10 department of base salary](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/0dbb6096-9760-4e37-a352-378b1b37f17b)

These insights highlight the variation in average base salaries across different departments, providing an overview of the salary distribution within the organization.

3.7 Top 5 Divisions based on 2020 Overtime Pay Distribution

![2020 division of base salary](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/6ed5f9c8-bc78-4049-a2e4-f8eae543e251)

The box plot aids in understanding the distribution and characteristics of overtime pay within the top divisions, facilitating data-driven insights into workforce management and compensation patterns.

3.8 Distribution of Base Salary based on Gender.

![Distribution of Base Salary by Gender](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/7fbfbc96-daa4-4edd-b663-5b8061b69878)

Overall, the kernel density plots offer a visual tool for comparing the distribution of base salaries by gender, allowing for insights into potential patterns, discrepancies, or commonalities in salary structures.

3.9 Heatmap of Top 10 Divisions vs Gender

![Heatmap](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/6b0aa1aa-c74c-4ade-9bec-2a0339ccc429)

Overall, the heatmap provides a clear and concise overview of the gender distribution within the top divisions, offering insights into potential areas for further analysis or targeted HR interventions.

# 4. Data Cleaning: 

4.1 Outlier Detection and Treatment:
Upon visual inspection of our box plot, we observed the presence of outliers within our dataset. To address this, we implemented a robust outlier detection and treatment approach using Z-score.

A) Z-score Method:
The Z-score method is a statistical technique used to identify outliers by measuring how many standard deviations an observation is from the mean. Observations with a Z-score greater than a specified threshold are flagged as outliers.

B) Winsorizing Technique:
To handle the identified outliers, we applied the winsorizing technique. Winsorizing involves capping extreme values by replacing them with less extreme values. Specifically, we set the lower cap at the 5th percentile and the upper cap at the 95th percentile of the data distribution.

C) Implementation:
Outlier Detection: We calculated the Z-scores for each data point.

D) Winsorizing: Data points below the 5th percentile were adjusted to the value at the 5th percentile, while those above the 95th percentile were adjusted to the value at the 95th percentile.
By applying the winsorizing technique, we effectively mitigated the impact of outliers on our dataset, ensuring robustness and reliability in our analysis.

# 5. Data Splitting and Preprocessing:

In this step, we split our dataset into features and the target variable. Our target variable, base salary (y), is separated from the features (X). We then utilize a ColumnTransformer for preprocessing, which allows us to apply various transformations selectively to different columns in our data. We've employed a OneHotEncoder within this transformer to encode categorical data. This preprocessing pipeline is specifically tailored to one-hot encode the categorical columns while leaving the non-categorical columns unchanged.

# 6. Model Selection and Evaluation:
6.1.1 MSE:

We've explored the performance of three different models: Support Vector Machine (SVM), Linear Regression, and Random Forest Regression. To evaluate these models, we've utilized the Mean Squared Error (MSE) metric. MSE quantifies the average squared difference between the actual and predicted values. A lower MSE indicates better model performance, signifying that the model's predictions are closer to the actual values.

![MSE](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/60c2d904-0db1-4828-b849-a22ffbf8256c)


6.1.2 Based on the MSE values:

a) Linear Regression MSE: 94727842.27752575

b) Random Forest Regressor MSE: 88475403.21661408

c) Support Vector Regressor MSE: 699046712.7006655

We can make the following observations about the accuracy of the models:
The Random Forest Regressor has the lowest MSE among the three models, indicating that it provides the most accurate predictions among them. The Linear Regression model has a higher MSE than the Random Forest model but lower than the Support Vector Regressor, suggesting that it performs moderately well in terms of accuracy. The Support Vector Regressor has the highest MSE, indicating that it provides the least accurate predictions among the three models.

6.2.1 R2 score:

![R2 score](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/5629722a-3d52-471f-8313-dbd947d5ed94)

We have also found R2 scores of all three models: 
The R^2 scores indicate how well the regression models fit the data:
Linear Regression R^2 Score: 0.8643
Random Forest Regression R^2 Score: 0.8732
Support Vector Regression (SVR) R^2 Score: -0.0015

6.2.2  For R^2 scores:

A score of 1 indicates a perfect fit.
A score of 0 indicates that the model performs no better than simply taking the mean of the target variable.
Negative scores indicate that the model performs worse than a horizontal line.

Given these scores:

Both Linear Regression and Random Forest Regression models have decent R^2 scores, indicating a good fit to the data.The Support Vector Regression (SVR) model has a negative R^2 score, which suggests that it performs worse than a horizontal line. This could mean that the SVR model is not suitable for this dataset or may require further tuning. In summary, the Linear Regression and Random Forest Regression models seem to provide reasonable fits to the data, while the SVR model may need further investigation or alternative approaches.

6.3 Precision, Recall and F1-score:

6.3.1 Precision:

Precision measures the accuracy of the positive predictions made by the model. It is the ratio of correctly predicted positive observations to the total predicted positives.
Precision = TP / (TP + FP)
TP (True Positives): The number of correctly predicted positive instances.
FP (False Positives): The number of incorrectly predicted positive instances.
Recall (also known as sensitivity or true positive rate):

6.3.2 Recall: 

Recall measures the ability of the model to find all the positive instances. It is the ratio of correctly predicted positive observations to the all actual positives in the dataset.
Recall = TP / (TP + FN)
FN (False Negatives): The number of incorrectly predicted negative instances.

6.3.3 F1-score:

F1-score is the harmonic mean of precision and recall. It provides a balance between precision and recall. F1-score reaches its best value at 1 and worst at 0.
F1-score = 2 * (Precision * Recall) / (Precision + Recall)
These metrics are commonly used in classification tasks to evaluate the performance of a model. 

6.3.4 F1, Precision and Recall score of Linear Regression: 

![LR1](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/d3cf1991-aae6-48d5-a989-76df2a2ff446)

6.3.5 F1, Precision and Recall score of Random Forest:

![F1 for RF](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/1f6c3ce5-84bb-436f-9a4c-30c92c8d5197)

6.3.6 F1, Precision and Recall score of SVM:

![F1 for SVM](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/dcbe0b97-8610-4ef4-b002-f29507c7185d)

The Random Forest Regression model shows the best performance with higher precision, recall, and F1-score compared to Linear Regression and SVR. The Support Vector Regression model (SVR) has notably lower precision, recall, and F1-score, indicating poorer performance compared to the other models. This may suggest that the SVR model is not well-suited for the given task or requires further optimization.

6.4 Confusion Matrix: 

A confusion matrix is a table that is often used to describe the performance of a classification model on a set of test data for which the true values are known. It allows visualization of the performance of an algorithm by showing the number of correct and incorrect predictions in each class.

Here's how a confusion matrix is typically structured for a binary classification problem:


![confusion matrix](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/8a952897-82ee-4722-81f6-0a8269c646fe)

Confusion Matrix of Random Forest and SVM:

![RF for CM](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/dd8fcf1b-7469-40a3-ac9d-8b983b4c0fab)

![SVM CM](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/9d755f3d-b450-4cfe-8f40-e0c8394fa24d)




# 7. Conclusion:
In conclusion, our project successfully addressed the business problem of predicting base salaries across different departments. Through extensive exploratory data analysis (EDA) and model evaluation, we gained valuable insights into the distribution of salaries, departmental characteristics, and the performance of different classifiers.
The classifiers, including Random Forest, Decision Tree, and Support Vector Machine, demonstrated varying levels of accuracy, with Random Forest exhibiting the highest predictive capability. Confusion matrices and actual vs. predicted comparisons provided a detailed understanding of the models' strengths and areas for improvement.
The project not only achieved its primary objective of creating a salary prediction model but also laid the groundwork for future refinements. Further enhancements may involve optimizing hyperparameters, exploring alternative algorithms, and incorporating additional features to boost model accuracy. Overall, our data-driven approach and machine learning solutions have contributed to informed decision-making regarding salary structures, potential pay disparities, and budget planning within the organization.


# 7. References:
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




