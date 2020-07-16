# Employee_Attrition_Analysis_Report
Employee Attrition Analysis Report - Understand why employees leave a company and apply various machine learning models to predict the next leaver!

## Objective
***
*My goal is to understand what factors contribute most to employee turnover and create a model that can predict if a certain employee will leave the company or not.*

*I’ll be following a typical data science pipeline :
1. **O**btaining the data is the first approach in solving the problem.

2. **S**crubbing or cleaning the data is the next step. This includes data imputation of missing or invalid data and fixing column names.

3. **E**xploring the data will follow right after and allow further insight of what our dataset contains. Looking for any outliers or weird data. Understanding the relationship each explanatory variable has with the response variable resides here and we can do this with a correlation matrix. 

4. **M**odeling the data will give us our predictive power on whether an employee will leave. 

5. I**N**terpreting the data is last. With all the results and analysis of the data, what conclusion is made? What factors contributed most to employee turnover? What relationship of variables were found? 

`##  3b. Correlation Matrix & Heatmap`
***
**Moderate Positively Correlated Features:** 
- projectCount vs evaluation: 0.349333
- projectCount vs averageMonthlyHours:  0.417211
- averageMonthlyHours vs evaluation: 0.339742

**Moderate Negatively Correlated Feature:**
 - satisfaction vs turnover:  -0.388375

**Stop and Think:**
- What features affect our target variable the most (turnover)?
- What features have strong correlations with each other?
- Can we do a more in depth examination of these features?

**Summary:**

From the heatmap, there is a **positive(+)** correlation between projectCount, averageMonthlyHours, and evaluation. Which could mean that the employees who spent more hours and did more projects were evaluated highly. 

For the **negative(-)** relationships, turnover and satisfaction are highly correlated. I'm assuming that people tend to leave a company more when they are less satisfied. 

### T-Test Result
***
The test result shows the **test statistic "t" is equal to -39.109**. This test statistic tells us how much the sample mean deviates from the null hypothesis. If the t-statistic lies **outside** the quantiles of the t-distribution corresponding to our confidence level and degrees of freedom, we reject the null hypothesis. We can check the quantiles with **stats.t.ppf()**

### T-Test Quantile
***
If the t-statistic value we calculated above **(-39.109)** is outside the quantiles, then we can reject the null hypothesis

### One-Sample T-Test Summary
***
#### **T-Test = -39.109**       |        **P-Value = 9.01e-279**       |       **Reject Null Hypothesis**

**Reject the null hypothesis because:**
 - T-Test score is outside the quantiles
 - P-value is lower than confidence level of 5%

Based on the statistical analysis of a one sample t-test, there seems to be some significant difference between the mean satisfaction of employees who had a turnover and the entire employee population. The super low P-value of **9.012e-279** at a 5% confidence level is a good indicator to **reject the null hypothesis**. 

But this does not neccessarily mean that there is practical significance. We would have to conduct more experiments or maybe collect more data about the employees in order to come up with a more accurate finding.

`##  3c. Distribution Plots (Satisfaction - Evaluation - AverageMonthlyHours)`
***
**Summary:** Let's examine the distribution on some of the employee's features. Here's what I found:
 - **Satisfaction** - There is a huge spike for employees with low satisfaction and high satisfaction.
 - **Evaluation** - There is a bimodal distrubtion of employees for low evaluations (less than 0.6) and high evaluations (more than 0.8)
 - **AverageMonthlyHours** - There is another bimodal distribution of employees with lower and higher average monthly hours (less than 150 hours & more than 250 hours)
 - The evaluation and average monthly hour graphs both share a similar distribution. 
 - Employees with lower average monthly hours were evaluated less and vice versa.
 - If you look back at the correlation matrix, the high correlation between evaluation and averageMonthlyHours does support this finding.
 
**Stop and Think:** 
 - Is there a reason for the high spike in low satisfaction of employees?
 - Could employees be grouped in a way with these features?
 - Is there a correlation between evaluation and averageMonthlyHours?

`##  3d. Salary V.S. Turnover`
***
**Summary:** This is not unusual. Here's what I found:
 - Majority of employees who left either had **low** or **medium** salary.
 - Barely any employees left with **high** salary
 - Employees with low to average salaries tend to leave the company.
 
**Stop and Think:** 
 - What is the work environment like for low, medium, and high salaries?
 - What made employees with high salaries to leave?

`##  3e. Department V.S. Turnover` 
***
**Summary:** Let's see more information about the departments. Here's what I found:
 - The **sales, technical, and support department** were the top 3 departments to have employee turnover
 - The management department had the smallest amount of turnover
 
**Stop and Think:** 
 - If we had more information on each department, can we pinpoint a more direct cause for employee turnover?

`##  3f. Turnover V.S. ProjectCount` 
***
**Summary:** This graph is quite interesting as well. Here's what I found:
 - More than half of the employees with **2,6, and 7** projects left the company
 - Majority of the employees who did not leave the company had **3,4, and 5** projects
 - All of the employees with **7** projects left the company
 - There is an increase in employee turnover rate as project count increases
 
**Stop and Think:** 
 - Why are employees leaving at the lower/higher spectrum of project counts?
 - Does this means that employees with project counts 2 or less are not worked hard enough or are not highly valued, thus leaving the company?
 - Do employees with 6+ projects are getting overworked, thus leaving the company?

`##  3g. Turnover V.S. Evaluation` 
***
**Summary:** 
 - There is a biomodal distribution for those that had a turnover. 
 - Employees with **low** performance tend to leave the company more
 - Employees with **high** performance tend to leave the company more
 - The **sweet spot** for employees that stayed is within **0.6-0.8** evaluation
 
 `##  3h. Turnover V.S. AverageMonthlyHours` 
 ***
 **Summary:** 
  - Another bi-modal distribution for employees that turnovered 
  - Employees who had less hours of work **(~150hours or less)** left the company more
  - Employees who had too many hours of work **(~250 or more)** left the company 
  - Employees who left generally were **underworked** or **overworked**.
  
  `##  3i. Turnover V.S. Satisfaction `
  ***
  **Summary:** 
   - There is a **tri-modal** distribution for employees that turnovered
   - Employees who had really low satisfaction levels **(0.2 or less)** left the company more
   - Employees who had low satisfaction levels **(0.3~0.5)** left the company more
   - Employees who had really high satisfaction levels **(0.7 or more)** left the company more
   
   `##  3j. ProjectCount VS AverageMonthlyHours` 
   ***

   **Summary:**
    - As project count increased, so did average monthly hours
    - Something weird about the boxplot graph is the difference in averageMonthlyHours between people who had a turnver and did not. 
    - Looks like employees who **did not** have a turnover had **consistent** averageMonthlyHours, despite the increase in projects
    - In contrast, employees who **did** have a turnover had an increase in averageMonthlyHours with the increase in projects

   **Stop and Think:** 
    - What could be the meaning for this? 
    - **Why is it that employees who left worked more hours than employees who didn't, even with the same project count?**
   
  `##  3k. ProjectCount VS Evaluation`
  ***
  **Summary:** This graph looks very similar to the graph above. What I find strange with this graph is with the turnover group. There is an increase in evaluation for employees who did more projects within the turnover group. But, again for the non-turnover group, employees here had a consistent evaluation score despite the increase in project counts. 

  **Questions to think about:**
   - **Why is it that employees who left, had on average, a higher evaluation than employees who did not leave, even with an increase in project count? **
   - Shouldn't employees with lower evaluations tend to leave the company more? 

`##  3l. Satisfaction VS Evaluation`
***
**Summary:** This is by far the most compelling graph. This is what I found:
 - There are **3** distinct clusters for employees who left the company
 
**Cluster 1 (Hard-working and Sad Employee):** Satisfaction was below 0.2 and evaluations were greater than 0.75. Which could be a good indication that employees who left the company were good workers but felt horrible at their job. 
 - **Question:** What could be the reason for feeling so horrible when you are highly evaluated? Could it be working too hard? Could this cluster mean employees who are "overworked"?

**Cluster 2 (Bad and Sad Employee):** Satisfaction between about 0.35~0.45 and evaluations below ~0.58. This could be seen as employees who were badly evaluated and felt bad at work.
 - **Question:** Could this cluster mean employees who "under-performed"?

**Cluster 3 (Hard-working and Happy Employee):** Satisfaction between 0.7~1.0 and evaluations were greater than 0.8. Which could mean that employees in this cluster were "ideal". They loved their work and were evaluated highly for their performance. 
 - **Question:** Could this cluser mean that employees left because they found another job opportunity?

`##  3m. Turnover V.S. YearsAtCompany `
***
**Summary:** Let's see if there is a point where employees start leaving the company. Here's what I found:
 - More than half of the employees with **4 and 5** years left the company
 - Employees with **5** years should **highly** be looked into 
 
**Stop and Think:** 
 - Why are employees leaving mostly at the **3-5** year range?
 - Who are these employees that left?
 - Are these employees part-time or contractors? 

`## 3n. K-Means Clustering of Employee Turnover`
***
**Cluster 1 (Blue):** Hard-working and Sad Employees

**Cluster 2 (Red):** Bad and Sad Employee 

**Cluster 3 (Green):** Hard-working and Happy Employee 

**Clustering PROBLEM:**
    - How do we know that there are "3" clusters?
    - We would need expert domain knowledge to classify the right amount of clusters
    - Hidden unknown structures could be present

`# 4. Modeling the Data`
***
 The best model performance out of the four (Decision Tree Model, AdaBoost Model, Logistic Regression Model, Random Forest Model) was **Random Forest**! 
 
 **Note: Base Rate** 
 ***
 - A **Base Rate Model** is a model that always selects the target variable's **majority class**. It's just used for reference to compare how better another model is against it. In this dataset, the majority class that will be predicted will be **0's**, which are employees who did not leave the company. 
 - If you recall back to **Part 3: Exploring the Data**, 24% of the dataset contained 1's (employee who left the company) and the remaining 76% contained 0's (employee who did not leave the company). The Base Rate Model would simply predict every 0's and ignore all the 1's. 
 - **Example**: The base rate accuracy for this data set, when classifying everything as 0's, would be 76% because 76% of the dataset are labeled as 0's (employees not leaving the company).

`**Note: Evaluating the Model**`
***
**Precision and Recall / Class Imbalance**

This dataset is an example of a class imbalance problem because of the skewed distribution of employees who did and did not leave. More skewed the class means that accuracy breaks down. 

In this case, evaluating our model’s algorithm based on **accuracy** is the **wrong** thing to measure. We would have to know the different errors that we care about and correct decisions. Accuracy alone does not measure an important concept that needs to be taken into consideration in this type of evaluation: **False Positive** and **False Negative** errors. 

**False Positives (Type I Error)**: You predict that the employee will leave, but do not

**False Negatives (Type II Error)**: You predict that the employee will not leave, but does leave

In this problem, what type of errors do we care about more? False Positives or False Negatives?

`**Note: Different Ways to Evaluate Classification Models**`
***
  1.  **Predictive Accuracy:** How many does it get right?
  2. **Speed:** How fast does it take for the model to deploy? 
  3. **Scalability:** Can the model handle large datasets?
  4. **Robustness:** How well does the model handle outliers/missing values?
  5. **Interpretability:** Is the model easy to understand?

`# Feature Importance`
***

**Top 3 Features:**
1. Satisfaction
2. YearsAtCompany
3. Evaluation

`# 5. Interpreting the Data`
***

**Summary:** 
`With all of this information, this is what HR should know about his company and why employees probably left:`
 1. Employees generally left when they are **underworked** (less than 150hr/month or 6hr/day)
 2. Employees generally left when they are **overworked** (more than 250hr/month or 10hr/day)
 3. Employees with either **really high or low evaluations** should be taken into consideration for high turnover rate
 4. Employees with **low to medium salaries** are the bulk of employee turnover
 5. Employees that had **2,6, or 7 project count** was at risk of leaving the company
 6. Employee **satisfaction** is the highest indicator for employee turnover.
 7. Employee that had **4 and 5 yearsAtCompany** should be taken into consideration for high turnover rate
 8. Employee **satisfaction**, **yearsAtCompany**, and **evaluation** were the three biggest factors in determining turnover.

`## Potential Solution`
***
**Binary Classification**: Turnover V.S. Non Turnover

**Instance Scoring**: Likelihood of employee responding to an offer/incentive to save them from leaving.

**Need for Application**: Save employees from leaving

In our employee retention problem, rather than simply predicting whether an employee will leave the company within a certain time frame, we would much rather have an estimate of the probability that he/she will leave the company. 
We would rank employees by their probability of leaving, then allocate a limited incentive budget to the highest probability instances. 

Consider employee turnover domain where an employee is given treatment by Human  Resources because they think the employee will leave the company within a month, but the employee actually does not. This is a false positive. This mistake could be expensive, inconvenient, and time consuming for both the Human Resources and employee, but is a good investment for relational growth. 

Compare this with the opposite error, where Human Resources does not give treatment/incentives to the employees and they do leave. This is a false negative. This type of error is more detrimental because the company lost an employee, which could lead to great setbacks and more money to rehire. 
Depending on these errors, different costs are weighed based on the type of employee being treated. For example, if it’s a high-salary employee then would we need a costlier form of treatment? What if it’s a low-salary employee? The cost for each error is different and should be weighed accordingly. 
 
 **Solution 1:**
 - `We can rank employees by their probability of leaving, then allocate a limited incentive budget to the highest probability instances.`
 - `OR, we can allocate our incentive budget to the instances with the highest expected loss, for which we'll need the probability of turnover.`

**Solution 2:** 
Develop learning programs for managers. Then use analytics to gauge their performance and measure progress. Some advice:
 - `Be a good coach`
 - `Empower the team and do not micromanage`
 - `Express interest for team member success`
 - `Have clear vision / strategy for team`
 - `Help team with career development`    

`## What Now?`
***
This problem is about people decision. When modeling the data, we should not be using this predictive metric as a solution decider. But, we can use this to arm people with much better relevant information for better decision making.

We would have to conduct more experiments or collect more data about the employees in order to come up with a more accurate finding. I would recommend to gather more variables from the database that could have more impact on determining employee turnover and satisfaction such as their distance from home, gender, age, and etc.

**Reverse Engineer the Problem**
***
After trying to understand what caused employees to leave in the first place, we can form another problem to solve by asking ourselves 
1. **"What features caused employees stay?** 
2. **"What features contributed to employee retention?**
**
`There are endless problems to solve!!!`
