# AnalyticAlle

# 1. Introduction
This README describes work done on the "Employee Compensation and Satisfaction Insights" Dataset. Resources used include Python and associated packages Google Colab, matplotlib, Seaborn, scikit-learn, statsmodels, and SciPy.
The analysis takes the form of a single Google Colab notebook of filename given above. To view this file, download it from this repository.
All images intended for inclusion in this README are located in the images subdirectory of this repository.
I have tried to structure the Google Colab notebook and this README so that they have corresponding sections. However, I do not wish to merely repeat here what has been stated in the notebook. I will endeavour to have this README summarize the work of the notebook and, hopefully, complement the analyses done there.

# 2. Description of the dataset
Predictive analysis is a form of analytics that employs statistical and machine learning techniques to recognize patterns and forecast outcomes. By scrutinizing historical and current data, predictive data analysis identifies trends and behaviours, enabling proactive decision-making for the future. This proactive approach assists businesses in minimizing risks and seizing opportunities, ultimately enhancing the decision-making process. In the context of our dataset, which encompasses information about departmental attributes, employee demographics, and salary-related variables, our objective is to construct a model capable of predicting salaries across varius departments within an organization. This endeavour aims to streamline salary structures, pinpoint potential pay disparities, and contribute to effective budget planning. Additionally, machine learning models can provide valuable insights to the HR department regarding salary distribution and compensation fairness.

# 2.1 Initial steps
I often use sites such as Medium.com to see how other people have investigated data sets using Python. The very first step is always to check if the data needs cleaning by looking for duplicate rows, zero values or NaNs where they shouldn't be etc. The head of the data set looks like:
![head of our dataset](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/d8afebcf-29bb-4c87-a01e-abb075c2a22a)

# 2.2 Descriptive statistics
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

# 2.3 Plots to summarize some statistics


![top 10 grade](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/4eef41ce-98cb-47b8-911c-2dccbe2512e0)

15: This grade occurs 1125 times and is the most frequently assigned grade in the dataset.        
20: This grade appears 314 times in the dataset. 
The 'grade' column in the dataset represents the classifications assigned to employees based on their roles or positions within the organization. Each unique grade signifies a specific level of responsibility, skill requirements, or seniority.

![Distribution of gender](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/2505ec42-d4bd-417c-92b5-215eb2ee7244)

The 'gender' column in the dataset indicates the distribution of employees based on their gender. In summary, the 'gender' distribution in the dataset suggests a higher representation of male employees compared to female employees. This information can be valuable for understanding the gender composition within the workforce and may be considered in various analyses or decision-making processes related to gender diversity and inclusion. Overall, gender distribution insights are valuable for organizations aiming to foster diversity and make data-driven decisions related to human resources and workforce management.

![Top 10 divisions](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/0db5cdde-cd36-4795-875c-9a99aee17dc0)

School Health Services has the highest count among the top 10 departments, indicating that it has a significant presence within the organization. 
Transit Gaithersburg Ride On and Transit Silver Spring Ride On are transit-related departments, suggesting that transportation services are substantial aspects of the organization's operations.
Office of Eligibility and Support Services is also prominently featured, indicating a focus on providing eligibility and support services, possibly related to social welfare or assistance programs.
Highway Services is another notable department, highlighting the organization's involvement in managing highways or road infrastructure.

![Distribution of base salary](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/d4715573-f869-469d-81d0-f3c1a09fd571)

The histogram depicts the distribution of base salaries among employees in the dataset. Insights from the histogram suggest that the dataset primarily consists of employees with salaries in the lower to mid-range, with a substantial concentration of around $50,000. 
The distribution reveals a skewed pattern, indicating that a smaller proportion of employees receive higher salaries, with a peak of around $100,000. 
This information can be valuable for understanding the salary distribution within the organization and may guide decision-making related to compensation and budget planning.


![Distribution of longevity of pay](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/0e1f5448-baab-4c81-9ea9-9188de526131)

These insights suggest that the majority of employees did not receive or received very less longevity pay in 2020, with a smaller percentage receiving varying amounts, as indicated by the specified bins in the displot.

![Top 10 department of base salary](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/0dbb6096-9760-4e37-a352-378b1b37f17b)

These insights highlight the variation in average base salaries across different departments, providing an overview of the salary distribution within the organization.

![2020 division of base salary](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/6ed5f9c8-bc78-4049-a2e4-f8eae543e251)

The box plot aids in understanding the distribution and characteristics of overtime pay within the top divisions, facilitating data-driven insights into workforce management and compensation patterns.

![Distribution of Base Salary by Gender](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/7fbfbc96-daa4-4edd-b663-5b8061b69878)

Overall, the kernel density plots offer a visual tool for comparing the distribution of base salaries by gender, allowing for insights into potential patterns, discrepancies, or commonalities in salary structures.

![Heatmap](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/6b0aa1aa-c74c-4ade-9bec-2a0339ccc429)

Overall, the heatmap provides a clear and concise overview of the gender distribution within the top divisions, offering insights into potential areas for further analysis or targeted HR interventions.

# 2.4 Data Cleaning: 
Outlier Detection and Treatment:
Upon visual inspection of our box plot, we observed the presence of outliers within our dataset. To address this, we implemented a robust outlier detection and treatment approach using Z-score.

A) Z-score Method:
The Z-score method is a statistical technique used to identify outliers by measuring how many standard deviations an observation is from the mean. Observations with a Z-score greater than a specified threshold are flagged as outliers.

B) Winsorizing Technique:
To handle the identified outliers, we applied the winsorizing technique. Winsorizing involves capping extreme values by replacing them with less extreme values. Specifically, we set the lower cap at the 5th percentile and the upper cap at the 95th percentile of the data distribution.

C) Implementation:
Outlier Detection: We calculated the Z-scores for each data point.

D) Winsorizing: Data points below the 5th percentile were adjusted to the value at the 5th percentile, while those above the 95th percentile were adjusted to the value at the 95th percentile.
By applying the winsorizing technique, we effectively mitigated the impact of outliers on our dataset, ensuring robustness and reliability in our analysis.


# 6. Conclusion:
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






