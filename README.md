## Project Name : Salary Prediction and Analysis

![salary image](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/1679ab76-cd56-449a-b2e1-4bce434b304b)
          
# 1. Introduction:
This README describes work done on the "Employee Compensation and Satisfaction Insights" Dataset. 

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
Upon visual inspection of our box plot, we observed the presence of outliers within our dataset. To address this, we implemented a robust outlier detection and treatment approach using Z-score. After removing outliers, it came to our notice that approximately 90% of our data got lost. Hence Outliers are not always bad. We have done analysis with and without outliers.

Shape of our datset with outliers :

![test1](https://github.com/Mervin50/ML_Project1_Employee_Compensation_and_Satisfaction_Insights/assets/167336864/5ef1c414-59bc-4766-a8d2-0a46e594e5b4)

Shape of our dataset after removing outliers:

![test2](https://github.com/Mervin50/ML_Project1_Employee_Compensation_and_Satisfaction_Insights/assets/167336864/dbbda02a-1a0f-487e-bdf6-607f8a06c2bd)


##### 4.1.1 Z-score Method:
The Z-score method is a statistical technique used to identify outliers by measuring how many standard deviations an observation is from the mean. Observations with a Z-score greater than a specified threshold are flagged as outliers.

##### 4.1.2 Winsorizing Technique:
To handle the identified outliers, we applied the winsorizing technique. Winsorizing involves capping extreme values by replacing them with less extreme values. Specifically, we set the lower cap at the 5th percentile and the upper cap at the 95th percentile of the data distribution.

##### 4.1.3 Implementation:
Outlier Detection: We calculated the Z-scores for each data point.

##### 4.1.4 Winsorizing: 
Data points below the 5th percentile were adjusted to the value at the 5th percentile, while those above the 95th percentile were adjusted to the value at the 95th percentile.

##### 5. Preprocessing with outliers:
##### 5.1 One-Hot Encoding :
We are doing One-Hot Encoding to convert categorical variables are converted into binary vectors.

![test1](https://github.com/Mervin50/ML_Project1_Employee_Compensation_and_Satisfaction_Insights/assets/167336864/cb356266-e4f3-44ce-a9d2-afb6d7501222)

##### 5.2 Label Encoding :
Label encoding is a technique in machine learning for converting categorical data into numerical form. We used label encoder on gender column.

![test1](https://github.com/Mervin50/ML_Project1_Employee_Compensation_and_Satisfaction_Insights/assets/167336864/11bb956d-7359-4b56-ab60-838a0d329ee1)

##### 5.3 Standarization : 
First, we split data. Then we do standarization of data, so that all the values come on a common scale.

x_train standarized data : 

![test1](https://github.com/Mervin50/ML_Project1_Employee_Compensation_and_Satisfaction_Insights/assets/167336864/a56060ad-195a-4a51-8ce6-97f98c583b6d)


x_test standarized data :

![test2](https://github.com/Mervin50/ML_Project1_Employee_Compensation_and_Satisfaction_Insights/assets/167336864/f841f08e-d3bb-4e67-b8c6-28930d1de81c)


# 6. Model Training and Evaluation with outliers: 

##### 6.1 Model Training: 
We used Logisitc Regression, Decision Tree, Random Forest and Support Vector Machine to train our model.

##### 6.2 Model Evaluation: 
Our MSE scores are : 

![test1](https://github.com/Mervin50/ML_Project1_Employee_Compensation_and_Satisfaction_Insights/assets/167336864/41eb18b4-1137-4aa2-88d7-534eeb02bcd2)

Our MSE scores are bad for all four models.

# 7. Preprocessing after Removing Outliers

##### 7.1 One-Hot Encoding after removing outliers : 

![test1](https://github.com/Mervin50/ML_Project1_Employee_Compensation_and_Satisfaction_Insights/assets/167336864/332d1281-c30d-4b1e-aa04-35c5f5231e70)


##### 7.2 Label Encoding after removing outliers:

![test2](https://github.com/Mervin50/ML_Project1_Employee_Compensation_and_Satisfaction_Insights/assets/167336864/c51a7c32-b23e-4e3e-bc1c-6b315a4e123e)

##### 7.3 Standarization after removing outliers:
We need to bring all the values of each column onto a common scale which will help us to train our model effiency.

Our x_train after standarization :

![test1](https://github.com/Mervin50/ML_Project1_Employee_Compensation_and_Satisfaction_Insights/assets/167336864/884b1a3f-e750-4159-b985-3bedbab0fad2)


Our x_test after standarization :

![test2](https://github.com/Mervin50/ML_Project1_Employee_Compensation_and_Satisfaction_Insights/assets/167336864/acb275a8-52bf-4920-b9df-2e35c8b378de)

# 8. Model training and Evaluation without outliers: 

##### 8.1 Model training without outliers: 
We used Logisitc Regression, Decision Tree, Random Forest and Support Vector Machine to train our model.

##### 8.2 Model Evaluation without Outliers : 

![test1](https://github.com/Mervin50/ML_Project1_Employee_Compensation_and_Satisfaction_Insights/assets/167336864/3c0bd66a-1ea5-4bed-b402-d75bf9e741f7)

Our MSE scores are bad for all four models.

# 9. Conclusion:

This project is for academic purpose. The MSE scores are bad, hence our model does not classify well. We tried training our model with outliers and without outliers. For both cases, there was not much difference.


