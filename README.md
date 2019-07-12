
# Hypothesis Testing With Northwind SQL Database

## The Project

For this project, we worked with the Northwind database--a free, open-source dataset created by Microsoft containing data from a fictional company in an SQL Database. Here's the schema for the Northwind database:

<img src='Northwind_ERD.png'>

The goal of this project is to use statistical analysis and hypothesis testing to generate analytical insights that can be of value to the Northwind company.

<a href="https://github.com/lpilossoph/dsc-2-final-project-online-ds-ft-112618/blob/master/Untitled.ipynb"> ### Link to Notebook ###</a>

## Post-Data Inspection Questions:

1. Do discounts have a statistically significant effect on the number of products customers order? If so at what level?
2. Do certain employees sell more products than others?
3. Do certain countries order more products than others?
4. Do clients buy more meat items or vegetarian items?

## Hypothesis Testing and Statistical Analyses:

### Question 1a: 
#### Do discounts have a statistically significant effect on the number of products customers order?
𝐻a: The average quantity of products purchased per order increases when a discount is applied. (H1: μ1 < μ2)
𝐻o: The average quantity of products ordered is equal to or less than when a discount is applied. (H0: μ1 >= μ2) 

### RESULT: REJECT THE NULL HYPOTHESIS
Explanation:
* Levene test: The p-value > alpha value, therefore the assumption of equal variance is fulfilled
* Two Sample T-Test: the p-value < alpha value, therefore we can REJECT the null hypothesis and conclude:
#### There is a significant increase in quantity of products ordered when a discount is applied.

### Question 1b: 
#### If discounts show a statistical significance on the quantity of products ordered, at what level(s) of discount do we see the significance?
𝐻a: The average quantity of products purchased changes depending on level of discount. (μ1 ≠ μ2 ≠ μ3 ... ≠ μk)
𝐻o: The average quantity of products purchase is unchanged at any level of discount. (μ1 = μ2 = μ3 ... = μk)

### RESULT: REJECT THE NULL HYPOTHESIS
Explanation:
* Levene test: p-value < alpha, therefore the assumption of equal variance among discount groups is not fulfilled**
* Kruskal-Wallis H test: p-value < alpha to test for significance among the groups using the median, since the assumption of equal variance was not fulfilled. Result shows there is indeed a significant difference among the groups. However, this test does not tell us the specific differences between each group. For that, we will have to run an ANOVA even though the assumptions equal variance are not technically fulfilled.
* ANOVA: F statistic value is 9.04 and that the P value < alpha showing that the null hypothesis is rejected in favor of the alternative hypothesis, indicating there is a significant difference among discount groups.
* Tukey test: show that the mean difference in quantity purchased is most significant when comparing no discount to a 5%, 15%, 20%, and 25% discount. The biggest increase in mean quantity purchased occurs at the 15% level, followed closely by the 25% and 5% level.
#### There is a significant increase in quantity of products ordered between levels of discounts

### Question 2: 
#### Do certain employees sell more products than others per transaction?
Certain employees have a significant impact on the quantity of products purchased. 𝐻a: μ1 ≠ μ2 ≠ μ3 ... ≠ μk
The specific employee has no impact on the quantity of products purchased. 𝐻o: μ1 = μ2 = μ3 ... = μk


### RESULT: FAILURE TO REJECT THE NULL HYPOTHESIS
Explanation:
* Levene test: p-value > alpha, therefore the assumption of equal variance among discount groups is fulfilled.
* ANOVA: F statistic value is 1.57 and the P value > alpha, showing that the null hypothesis cannot be rejected in favor of the alternative hypothesis, indicating there is no significant difference among employees sale numbers.
* Tukey Test: confirms ANOVA results, as it fails to reject the null hypothesis with all comparisons
#### There is no significant difference in quantity of products sold per order between the nine employees of Northwind Trading.


### Question 3: 
#### Do certain countries purchase more products than others per order?
𝐻a: Customers from specific countries purchase a significantly different amount of products per order than others. (μ1 ≠ μ2 ≠ μ3 ... ≠ μk)
𝐻o: The customers from each country purchase the same average quantity of products per order. (μ1 = μ2 = μ3 ... = μk)

### RESULT: REJECT THE NULL HYPOTHESIS
Explanation:
* Levene test: p-value < alpha, indicating that the samples do not fulfill the assumption of equal variance
* Kruskal-Wallis H test: there is a statistically significant difference among the quantities of items purchased per transaction between different countries.
#### There is a significant difference in quantity of products ordered depending on the country it is ordered from.

### Question 4: 
#### Do clients purchase significantly more meat or vegetarian items?
𝐻a: There is a difference between the average quantity of meat vs. vegetarian items purchased. (H1: μ1 ≠ μ2)
𝐻o: There is no difference between the average quantity of meat vs. vegetarian items purchased. (H0: μ1 = μ2)¶

### RESULT: FAILURE TO REJECT THE NULL HYPOTHESIS
Explanation:
* Levene test: p-value > alpha value, therefore the assumption of equal variance is fulfilled
* Two Sample T-Test: p-value > alpha, therefore we CANNOT REJECT the null hypothesis and we can conclude:
There is no significant difference in quantity of vegetarian products ordered vs. meat products ordered per order.¶

## Conclusions:
* Discounts do in fact have an effect on the quantity of items purchased per order. There is an approximately 20% increase in the number of items ordered when a 15% discount is applied to items, and an approximately 19% increase when a 5% discount is applied to items, relative to no discount.
* Specific Employees have no effect on the quantity of items purchased per transaction. However, certain employees have overall sold more items and have brought in more money compared to others, but this may be attributed to hire-date.
* Certain countries purchase significantly more quantity of items per transaction than others. Germany purchases approximately 25% more items per transaction than the UK.
* There is no statistically significant difference between the number of vegetarian items purchased per transaction and the number of meat products purchased per transaction.

## Future Work
* Examine specific customer trends since our linear regression showed this to be a significant predictor of the quantity of items ordered per transaction.
* Examine employee sales adjusting for hire-date to determine if there are any employees bringing in more money.
* Examine the relationships between other types of products and thier sales numbers to determine whether or not they sell better than others.






 
