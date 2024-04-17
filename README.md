# AnalyticAlle
# 1. Introduction

This README describes work done on the "Employee Compensation and Satisfaction Insights" Dataset. Resources used include Python and associated packages Google Colab, matplotlib, Seaborn, scikit-learn, statsmodels, and SciPy.
The analysis takes the form of a single Google Colab notebook of filename given above. To view this file, download it from this repository.
All images intended for inclusion in this README are located in the images subdirectory of this repository.
I have tried to structure the Google Colab notebook and this README so that they have corresponding sections. However, I do not wish to merely repeat here what has been stated in the notebook. I will endeavour to have this README summarize the work of the notebook and, hopefully, complement the analyses done there.

#2. Description of the data set

Predictive analysis is a form of analytics that employs statistical and machine learning techniques to recognize patterns and forecast outcomes. By scrutinizing historical and current data, predictive data analysis identifies trends and behaviours, enabling proactive decision-making for the future. This proactive approach assists businesses in minimizing risks and seizing opportunities, ultimately enhancing the decision-making process. In the context of our dataset, which encompasses information about departmental attributes, employee demographics, and salary-related variables, our objective is to construct a model capable of providing insights of what is influencing employee compensation and job satisfication within an organization. This endeavour aims to streamline salary structures, pinpoint potential pay disparities, and contribute to effective budget planning. Additionally, machine learning models can provide valuable insights to the HR department regarding salary distribution and compensation fairness.

2.1 Initial steps

I often use sites such as Medium.com to see how other people have investigated data sets using Python. The very first step is always to check if the data needs cleaning by looking for duplicate rows, zero values or NaNs where they shouldn't be etc. The head of the data set looks like:
![head of our dataset](https://github.com/Mervin50/AnalyticAlley5/assets/167336864/d8afebcf-29bb-4c87-a01e-abb075c2a22a)
