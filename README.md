
# Hypothesis Testing With Northwind SQL Database



### The Project

For this project, we worked with the Northwind database--a free, open-source dataset created by Microsoft containing data from a fictional company in an SQL Database. Here's the schema for the Northwind database:

<img src='Northwind_ERD.png'>

The goal of this project is to use statistical analysis and hypothesis testing to generate analytical insights that can be of value to the Northwind company. 

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


 
