# Churn Predictions of Bank Customers in Europe

This is my first serious repository to document my works or projects.

In this project, I used a dummy data about Bank Customers from a Bank which have branches in France, Spain, and Germany. This data contains various information about bank customers that hopefully can predict the customers will churn or not. There are 10 independent features which can be used as predictors:
- `CreditScore`; 
- `Geography`;
- `Gender`;
- `Age`;
- `Tenure`;
- `Balance`;
- `NumOfProducts`;
- `HasCrCard`;
- `IsActiveMember`;
- `EstimatedSalary`.
To do the churn prediction, first I identify the target (dependent) column which is `Exited` column. Then I used Statistics Descriptive to find out the distribution of data in each column. Next in modelling step, I used 3 models that is Logistic Regression, Decision Tree, and Random Forest. I used those 3 models without hyper parameter tuning to predict the churn of customers. I used metrics in confusion matrix, such as Precision, Recall, and Accuracy to determine the best model. I got the Random Forest model as the best model, then I used this model to create the conclusion in the analysis step.

## Target Description
Here I use Target Variable in column `Exited`.

![gambar](https://user-images.githubusercontent.com/52767438/222882655-57ecf397-f36f-4198-a6d8-be189566a3df.png)

On Target Variable, I defined: 
- 0 = Not Churn (Stay); 
- 1 = Churn.

Next, I see how many customers choose to churn or stay.

![gambar](https://user-images.githubusercontent.com/52767438/222882693-36aba0b7-cd86-4e63-a2e4-dd6b5ed938e5.png)

Customers who choose to stay (Not Churn) have a higher proportion than customers who choose to churn, the proportion is respectively 80:20. Indicates that there are still more customers who like the products at the bank.
Next, we look at the characteristics of each independent variable on the customer's "Churn" condition.

## Statistics Descriptive
### 1. Credit Score Feature

![gambar](https://user-images.githubusercontent.com/52767438/222882823-431ad03d-127f-4531-b0b9-0e6110fc4d87.png)

Churn customers have a slightly smaller average credit compared to customers who choose to stay. Even so, the difference in the average credit score for customers who stay and churn is not too different.

### 2. Tenure Feature

![gambar](https://user-images.githubusercontent.com/52767438/222883018-2bbb14a1-d222-4b5c-b734-373eade6cbfa.png)

*The unit of Tenure Feature is defined as month.*
Both customers who choose to churn or not, have an average product usage of around 5 months.

### 3. Num of Products Feature

![gambar](https://user-images.githubusercontent.com/52767438/222883241-248e32e4-7901-4097-8473-0e5f2833cfc0.png)

Customers who choose to stay have greater total product usage compared to customers who churn. However, this figure is highly dependent on the number of customers in each category.

![gambar](https://user-images.githubusercontent.com/52767438/222883330-e8fd44ef-70a6-44ee-a86a-3262afe30772.png)

So, when viewed from the average use of the number of products, the two types of customers both have an average number of product uses around 1.5, or both types of customers use an average of 1 to 2 bank products.

### 4. Geography Feature
There are only 3 countries in this dataset: Germany, France, and Spain. Here is the customer distribution between those 3 countries:

![gambar](https://user-images.githubusercontent.com/52767438/222883504-8b284017-65cb-4930-b967-401bccf20c9b.png)

The distribution of customer who is churn or not based on `Geography` feature:

![gambar](https://user-images.githubusercontent.com/52767438/222883569-c73fa4c4-232c-47a1-99e9-3c5eac6b67bf.png)

![gambar](https://user-images.githubusercontent.com/52767438/222883587-e1c8dbe6-3c8e-415e-ba08-2a8c804a72b2.png)

About half of the total number of customers are from France, but customers from Germany have about twice the proportion of customers who churn than customers from France and Spain.

### 5. Balance Feature

![gambar](https://user-images.githubusercontent.com/52767438/222883608-ed4c890b-f8c8-4e53-9ee8-2b36a8d5c5ad.png)

*The currency used is defined as the Euro because geographically, customers come from 3 European countries.*
It can be seen that customers who are churn actually have a fairly high average balance compared to customers who are stay. The difference is quite high, which is around 20,000 Euros.

### 6. Estimated Salary Feature

![gambar](https://user-images.githubusercontent.com/52767438/222883752-cb966098-19e9-4a32-8569-7585e483e983.png)

*The currency used is defined as the Euro because geographically, customers come from 3 European countries.*
Estimated salary (income) of customers who churn has an average higher than customers who choose to stay. Even so, the difference is not as big as Balance Feature, which is around 2,000 Euros.

### 7. Gender Feature
Here is the customers distribution based on `Gender`:

![gambar](https://user-images.githubusercontent.com/52767438/222883812-d980cf8d-0ac2-4cde-9ad3-172c66ef8c9f.png)

The distribution of customer who is churn or not based on `Gender` feature:

![gambar](https://user-images.githubusercontent.com/52767438/222883825-46c4ef43-0bb2-4dfb-bc5f-147430ed17ae.png)

![gambar](https://user-images.githubusercontent.com/52767438/222883831-f92843ae-a5c0-4168-9d41-d95b562bbb1d.png)

The proportion of male and female customers is not too different, but female customers have a greater proportion of churn than male customers.

### 8. Has Credit Card Feature
Here is the customers distribution based on `HasCrCard`:

![gambar](https://user-images.githubusercontent.com/52767438/222883907-245d5ad0-5d8c-4a91-a15a-929a4e407af8.png)

Defined:
- 0 = customer does not have credit card; 
- 1 = customer have credit card.

The distribution of customer who is churn or stay based on `HasCrCard` feature:

![gambar](https://user-images.githubusercontent.com/52767438/222883962-a853e85e-7c1b-4750-8dbe-6b38b2180ec5.png)

![gambar](https://user-images.githubusercontent.com/52767438/222883971-88aac794-e5b1-4f4f-8688-1c4c084e80b2.png)

Most customers have credit cards with a ratio of around 7:3. However, the proportion of customers who churn is not too different between customers who have credit cards and those who do not.

### 9. Active Member Feature
Here is the customers distribution based on `IsActiveMember`:

![gambar](https://user-images.githubusercontent.com/52767438/222885952-b9e947e8-6783-436b-ac68-ceff38eafb16.png)

Defined:
- 0 = not active member;
- 1 = active member.

The distribution of customer who is churn or stay based on `IsActiveMember` feature:

![gambar](https://user-images.githubusercontent.com/52767438/222885985-7da643d5-870f-4ed4-a277-7ae014d197d2.png)

![gambar](https://user-images.githubusercontent.com/52767438/222885994-10763d4c-7fed-4051-89e3-42130eba852b.png)

The number of customers who are active members is slightly more than those who are not active, and the proportion of customers who have churn is higher among customers who are not active members.

### 10. Generation
The Age variable is changed to a generational variable that classifies age groups based on their generation.
- Age less than up to 26 years: Gen Z
- Age between 27-40 years: Millenials Generation
- Age between 41-56 years: X Generation
- Age between 57-75 years: Baby Boomer Generation
- Age more than 75 years: Traditionalists Generation
Source: https://binus.ac.id/knowledge/2019/12/populasi-dunia-terbagi-dalam-berbagai-generasi-apa-saja/

Here is the customers distribution based on `Generation`:

![gambar](https://user-images.githubusercontent.com/52767438/222886055-063a5355-1e06-4000-8eab-276729a1526d.png)

The distribution of customer who is churn or stay based on `Generation` feature:

![gambar](https://user-images.githubusercontent.com/52767438/222886071-0c90dee9-e7b9-495c-81c6-b150b28b128a.png)

![gambar](https://user-images.githubusercontent.com/52767438/222886086-691d9e07-a587-45c8-beba-7ffd26d0f791.png)

In terms of numbers, customers who are Millennials Generation greatly dominate customers with a total of 5608 or more than half of the total customers. Followed by customers from Generation X, Baby Boomer Generation, Generation Z, and the least are Generation Traditionalists

However, the largest proportion of customers who churn are from Generation X and Baby Boomer Generation. Generation Z and Millennials have a relatively small proportion of churn with a proportion of less than 12%. Meanwhile, Generasi Traditionalists only had 1 customer who churn.

Because there are several age categories that have a small frequency in the churn customer category, especially the Traditionalist Generation, the Age variable will be used like a numerical variable. This is because to prevent information loss on this variable, because in a case of randomization of the train and test datasets, the Churned Traditionalist Generation may not be recorded in the train dataset. So the behavior patterns of the Traditionalist Generation who choose to churn cannot be predicted by the model.

## Feature Selection
Feature selection is carried out to identify which features will have a significant effect on the model or not. Two feature selections methods are used, namely the Chi-Square test for categorical independent variables and the Correlation Test for numerical variables.

### Chi-Square Test
Chi-Square Test aims to see the relationship between two categorical variables. Chi-square test can also see whether a categorical independent variable can affect the dependent variable or not.

An alpha error rate (α) of 5% is used to test the hypothesis as follows:
- H0 (initial hypothesis) is the independent variable has no effect on the dependent variable;
- H1 (alternative hypothesis) is the independent variable has an effect on the dependent variable.

The test statistic is used in the form of a P-Value (the probability of not rejecting H0). H0 is rejected if the P-Value < α (0.05).
Here is the result of Chi-Square Test for Categorical Independent Variables:

![gambar](https://user-images.githubusercontent.com/52767438/222886161-33f59c35-c70a-4fb9-90bf-ecabcbf702a8.png)

Almost all categorical variables have a P-Value greater than α (0.05), except for the `HasCrCard` variable. So that the HasCrCard variable is not included in the model formation.

### Correlation Numeric Independent Variables (Multicollinearity Test)
Multicollinearity is the term used when there is a relationship between numerical independent variables (interval and ratio scales).

The existence of multicollinearity causes the results of the analysis to be inconsistent because the slightest change in an independent variable will affect other related variables.

To detect the presence of multicollinearity, you can measure the correlation coefficient (r) of Pearson's Correlation for each numerical independent variable. The value of the correlation coefficient (r) ranges from -1 to 1. If the value of r is negative, then the correlation between the two variables is negative (one variable increases in value, the other variable decreases in value). If the value of r is positive, then the correlation between the two variables is positive (one increases in value, the other variable increases too). With the following scale (regardless of positive and negative):
- Value r 0.00 - 0.19 : Very Weak Correlation
- Value r 0.20 - 0.39 : Weak Correlation
- Value r 0.40 - 0.69 : Moderate Correlation
- Value r 0.70 - 0.89 : Strong Correlation
- Value r 0.90 - 1.00 : Very Strong Correlation

Source: https://geographyfieldwork.com/SpearmansRankCalculator.html

Correlation between variables is considered to have multicollinearity if the correlation coefficient (r) is more than 0.50 or Moderate Correlation to Very Strong Correlation.
Here is the result of Multicollinearity Test for Numerical Independent Variables:

![gambar](https://user-images.githubusercontent.com/52767438/222886294-5c107357-cf54-430c-907d-60aa57c9bed9.png)

![gambar](https://user-images.githubusercontent.com/52767438/222886302-92791041-5c21-48ac-b59e-711d65dd2e77.png)

It can be seen that the highest correlation is found in the correlation of the NumOfProducts VS Balance variable. But the value is still around -0.3 or Weak Correlation. So it can be said that there is no multicollinearity in the numerical independent variables in this dataset and all numerical variables can be included in the model formation.

## Used Features
Now, from two methods of feature selection, only `HasCrCard` that is not passed the chi-square test. So, all independent variables except `HasCrCard` will be included in modelling step.

## Data Transform
One Hot Encoding (dummy variable)

Machine Learning can only analyze numeric variables, but categorical variables are often found that are not numeric (such as gender). Then this variable must be translated into a number variable. Like Gender Male becomes 1 and Female becomes 0. This process is called Encoding.

If there are more than two categories in one variable, then the One-Hot Encoding method (dummy variable formation) can be used which can spread each category in a column into several columns. In this case, only `Geography` column have more than two categories for categorical variable. I encoded `Geography` so that it became like this:

![gambar](https://user-images.githubusercontent.com/52767438/222886541-bfbe5c71-91fc-465f-b344-48d7f2710e96.png)

It can be seen that the results for the Geography variable will appear in three new columns, each of which translates a category in the Geography variable (Germany, France, and Spain).

Now, I have to change gender variable from string type to integer type

![gambar](https://user-images.githubusercontent.com/52767438/222886671-597efe90-3aba-44dc-9181-0fecf4bf734a.png)

Gender Variable has been changed to integer and its new name is cod_gender

## Modelling
For modelling purpose, I split the data to train data and test data with ratio respectively 70:30

![gambar](https://user-images.githubusercontent.com/52767438/222886763-37c3a1dc-21fd-49a0-b1f4-282d6cbe84a7.png)

### 1. Logistic Regression
The Logistic Regression model allows to analyze the dependent variable in the form of ordinal data, so it is often included in the category of classification algorithms. After I train the data with Logistic Regression, here is the evaluation metrics:

![gambar](https://user-images.githubusercontent.com/52767438/222886801-38352972-0bf3-4cc2-83e9-e44d067f6028.png)

![gambar](https://user-images.githubusercontent.com/52767438/222886796-93a2f7f4-ad1c-4057-aa2f-30a3792dcfc2.png)

The Logistic Regression model that has been made has an accuracy of 81.8% or 81.8% of the test dataset can be correctly predicted by this model. This figure is pretty good because it means the model is not overfitting.

However, when looking at the Precision value, it can be seen that the value is only around 63.8%. This means that the model can correctly predict that only 63.8% of customers will churn.

Meanwhile, the Recall/Sensitivity value is also very small, namely 23.3%. This means that only 23.3% of churn customers were correctly predicted as churn customers. So that other methods can be used to get better results.

### 2. Decision Tree
Decision Tree Regression is a decision support that uses a graph or decision model like a tree along with the possible consequences based on the circumstances/decisions taken. Decision Tree Regression is one way to present an algorithm consisting only of conditional control statements. After I train the data with Decision Tree, here is the evaluation metrics:

![gambar](https://user-images.githubusercontent.com/52767438/222886831-71ffca0f-c962-4d49-9cf7-1b1c9f2d32e7.png)

![gambar](https://user-images.githubusercontent.com/52767438/222886835-639feff0-c045-4bef-b166-e816574bc0bd.png)

The Decision Tree model that has been created has an accuracy of 79.7% or 79.7% of the test dataset can be correctly predicted by this model. This figure is quite good, but still lower than the Logistic Regression accuracy value.

Likewise, when looking at the Precision value, it can be seen that the value is only around 49.7%. This means that the model can correctly predict that only 49.7% of customers will churn. This figure is also still smaller than the Logistic Regression model.

Meanwhile, the Recall/Sensitivity value is better than the Logistic Regression, which is 55.5%. This means that 55.5% of customers who churn are correctly predicted as churn customers. With a small accuracy value and small precision, other methods can be used to get better results.

### 3. Random Forest
Random Forest is a machine learning algorithm that uses a decision tree as a basis. Then the decision tree model is strengthened by an ensemble method called bagging. In other words, the Random Forest forms many Decision Trees which are then taken by combinations of rules from the Decision Trees that have been formed to form a more complex decision tree. After I train the data with Random Forest, here is the evaluation metrics:

![gambar](https://user-images.githubusercontent.com/52767438/222886857-09f2a567-8c43-48fc-ad9d-332ece6304d3.png)

![gambar](https://user-images.githubusercontent.com/52767438/222886861-e1cdac79-2bde-4ee9-9acf-4218f17624d7.png)

The Random Forest model that has been made has an accuracy of 86.7% or 86.7% of the test dataset can be correctly predicted by this model. This figure is the best figure among the three models used.

Likewise, when looking at the Precision value, it can be seen that the value is around 77.8%. This means that the model can correctly predict that customers will churn by 77.8%. This figure is also the largest figure among the other two models.

Meanwhile, the Recall/Sensitivity value is better than the Logistic Regression, which is 47.7%. This means that 47.7% of customers who churn are correctly predicted as churn customers. Even though the Decision Tree model still has a higher Recall value, the difference is not too big, namely not more than 10%. So the Random Forest model can be considered as the best model that can be taken

## Conclusion
To see the insights that can be drawn on the results of the Random Forest Classifier modeling, it can be seen from the Feature Importance value of each independent variable forming the model.

![gambar](https://user-images.githubusercontent.com/52767438/222886882-cb4779ea-e884-4993-80b9-5a1b98cf8a23.png)

![gambar](https://user-images.githubusercontent.com/52767438/222886887-6e6f0bcf-fc54-42f9-ba55-55cc9b97eb02.png)

In general, numeric variables have a higher Feature Importance value than categorical variables. Then among all the independent variables, the Age variable is the variable that has the highest importance value of 0.237. In terms of customer characteristics, it is known that customers are dominated by Millennial Generation customers (approximately > 58%). Also, the Millennials age category also has a fairly low percentage of churn, so this Bank's products include products that make Millennials feel at home and marketing can be focused on targeting the Millennials' market so that the potential for churn decreases.

![gambar](https://user-images.githubusercontent.com/52767438/222886900-5d53eb6e-73e5-4570-a503-d460d0570b43.png)

This must also be balanced by taking into account the Estimated Salary of the customer who has the second highest Feature importance value. The Millennials dominance factor causes the characteristic of the churn variable to have a higher average Estimated Salary, so that a small Salary does not mean customers will churn. This also means that the market for this Bank is actually Millennials, who have an average Estimated Salary that is relatively smaller than the Generation above.

Geography and Gender variables are the variables that have the least importance. So that country of origin and gender do not play too much a role in making decisions about whether to churn or not.

**Conclusion**: Focus on customers who are at the age of the Millennial Generation (27-40 years) by creating products or promotional programs that they like. Even though the average Estimated Salary of the Millennial Generation is quite small, with a large number and characteristics that are quite loyal to this Bank, it can be said that Millennials are a very potential market to target.
