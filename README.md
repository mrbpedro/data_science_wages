# Data science salaries

This is my explanatory analysis on Data Science average salaries around the world, taken from Kaggle. This analysis includes the so-called data cleaning, data wrangling, data visualization and hypothesis test in Python. Let's assume I am preparing the data for a machine learning model, so that I am interested in identifying the predictors of wages in the Data Science field. Hence, salary (*salary_in_usd*) would be our target variable.

## 1. General comments on data set

* It is not a large data set, containing only 11 columns and 607 observations. 
* Fortunately, there are no missings in any column.
* There is an *Unnamed* feature, like a second index, that should be dropped.
* Most potential predictors, like *job_title* or *employment_type*, are categorical variables, while the target variable (*salary_in_usd*) is continous. It requires especific ways to check correlations. Traditionally employed, neither scatter plot nor pierson correlation are suitable in this case.  

## 2. Actions taken for cleaning data and feature engineering

**Target variable**: Handling outliers and non normal distribution. 
* Log transformation.

**Job title**: I merged variations of 'Data scientists' (e.g Principal Data Scientist, Lead Data Scientist), 'Data Analyst', 'Data Engineer' into the main categories. 

**Company level**: There is an overrepresentation of interviewed people from United States, which accounts for almost 60% of the respondents, while no other country accounts for even 10%. Given this overrepresentation, an analysis covering all cases will produce biased findings. In this case, a more careful analysis should either focus only on the United States cases or on the other countries excluding the United States.

**Experience level**: There are more Senior professionals surveyed, which is reasonable, since it is an intermediare position between a begineer (Junior) and an Executive position. So the data tends to show the average wages according to the experience.  

## 3. Findings

* Based on absolute values, visualization shows that Data Architect has the highest average salary in US, but with a broad confident interval due to the few observations (just 9). 
* A more accurate analysis, based on weighted average, show that Data Engineers have the highest average salary in US, followed by Data Scientists and Data Analysts.

### 3.1 Beyond the United States 

In order to check variations among countries, I conducted an analysis taking account countries with more than 10 observations, excluding US. 

* In some places, Data Analysts earn more than Data Engineers and Data Scientist (Canadá); in others Data Scientist has the highest average wage (Spain) and, in turn, where Data Engineer has the highest average wage (Great Britain). This means that there is no pattern among countries, which is why machine learning models should regard the different demands in each country.


## 4. Hypothesis test

Exploratory analysis has shown that on average the salaries of Data Engineers are higher than those of Data Scientists in the United States. So I apply hypothesis testing in order to check whether this difference is not random. I use Test T which is aimed at testing averages differences between groups. 

Null hypothesis (H<sub>0</sub>) presumes that the difference observed between averages is random. Alternative hypothesis (H<sub>a</sub>) assumes that it is systematic.

*Conclusion*: Since the p_value of T-test is 0.68, i.e greater than 0.05, the test fails to reject the null hypothesis that difference between Data Engineer and Data Scientist is random.


