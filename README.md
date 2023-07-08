#INTRODUCTION

In this data science project, we aim to build a multiple linear regression model to predict house sale prices in King County, leveraging the King County House Sales dataset. The project's objective is to provide accurate estimates of property values to homeowners and potential buyers, enabling informed decision-making in the real estate market.

##BUSINESS AND DATA UNDERSTANDING

The real estate agency needs to understand the relationship between various features of the houses and their sale prices in order to provide accurate advice to homeowners. By performing multiple linear regression analysis on the King County House Sales dataset, the agency can identify which home renovation factors significantly impact the sale price.

The King County House Sales dataset contains comprehensive information about house sales, including features such as the number of bedrooms, number of bathrooms, square footage of living space in the home, number of floors in the house, how good the overall grade of the house is in relation to design and construction, whether the house has a waterfront view and the square footage of te lot. To better understand the dataset, we will perform exploratory data analysis, examine distributions, identify correlations, and assess feature importance.

###MODELING

This involves checking data to check if there exists any possible problems that makes data unsuitable for analysis.The problems may include missing data , duplicated data , handling categorical variables and obtaining the relevant subset from our dataset that are likely to have a significant impact on the target variable.Data cleaning and preparation done in our datasets include checking for missing values, dropping unnecessary columns, getting rid of duplicates,handling categorical variables and creating new dataframes that suit our study including subsetting our datasets.Each data cleaning process is described in details in each cell based on the dataset.

Feature Selection:

Selection of relevant features that are likely to have a significant impact on the target variable (sale price) has been done. Consider both numerical and categorical variables based on domain knowledge and correlation analysis. Drop any unnecessary or redundant columns.I will focus on a subset of the overall dataset.These features are:

price: sale price which is our prediction target

bedrooms: number of bed rooms in the house

bathrooms: number of bathrooms in the house

sqft_living: square footage of living space in the home

sqft_lot: square footage of the lot

floors: number of floors or the levels in the house

waterfront: whether the house is located on a water front

grade: overall house grade in relation to design and construction

In handling missing values we can observe from the summary statistics that the count for each column is 21597 which gives an implication that we do not have any missing data. So we are certain that we have evaded the dangers of performing multiple linear regression with missing data.Handling missing values before performing multiple linear regression is essential to ensure unbiased and accurate results, preserve sample size and statistical power, maintain data integrity, fulfill the assumptions of linear regression, enhance model performance, and enable fair comparisons and generalizability of the findings.

Checking for duplicates:

Duplicate observations can affect the regression model's results, as they may introduce bias and impact the statistical properties of the model.So we first check for duplicates and drop the duplicates but keep the first occurence.By dropping the duplicates, we ensure that each observation in our dataset is unique, which is important for reliable and accurate analysis in multiple linear regression.

Handling Categorical Variables:

First we inspect pandas data types in our dataset to know whethervwe will use all te columns.Object data type cannot be used because the model will crash.Convert categorical variables into numerical representations using technique called one-hot encoding. This ensures that the data can be properly utilized in the regression model.

Start with a simple linear regression

Regression models are evaluated against a "baseline". For simple linear regression, this baseline is an "intercept-only" model that just predicts the mean of the dependent variable every time. For multiple linear regression, we typically build a simple linear regression to be that baseline.

Since sqft_living is the feature with the strongest correlation, we will build a simple linear regression with that.

Multiple Regression with Many Features

We are now creating a model that uses all the columns from our sub setted data set that will help us evaluate the price of houses in King County.

####REGRESSION RESULTS

In analysing the results of our multiple regression model, we can look at the F-statistic p-value to see if it's statistically significant and the adjusted R-Squared to see the proportion of variance explained (around 62%).

The p value (0.00) is less than 0.05 thus we reject the null hypothesis and conclude that the model is statistically significant overall.

Our R-squared value is equal to 0.617 ,this means that the proportion of variance explained by our model out of the total variance is about 62%.This simply means 62% of the variation in price is explained by our model.

Here's a detailed analysis of the results:

const (5.849896e+05): This represents the intercept or constant term in the regression equation. This indicates the estimated average price when all other predictors are kept constant.The estimated price is 584,989.60 dollars.

bedrooms (-1.890175e+04): A negative coefficient suggests that an increase in the number of bedrooms is associated with a decrease in price, holding other variables constant. This coefficient value indicates the estimated change in price for each additional bedroom.So for each additional bedroom the price decreases by 18,901.75 dollars

bathrooms (8.325041e+01): A positive coefficient implies that an increase in the number of bathrooms is associated with an increase in price, assuming other variables remain constant. This coefficient value indicates the estimated change in price for each additional bathroom.Thus an increase in the number of bedroom results with an increase in house price by 83.25 dollars.

sqft_living (1.701378e+02): This coefficient represents the estimated change in price for each additional square foot of living space. A positive coefficient implies that larger living area tends to be associated with higher prices.

sqft_lot (-3.657163e-01): The negative coefficient suggests that an increase in the lot size is associated with a decrease in price, assuming other variables are held constant. This coefficient value represents the estimated change in price for each additional square foot of lot size.

floors (-2.498776e+04): A negative coefficient indicates that an increase in the number of floors is associated with a decrease in price, holding other variables constant. This coefficient value represents the estimated change in price for each additional floor.

waterfront_YES (7.952743e+05): This coefficient represents the estimated price increase for properties with a waterfront compared to those without. A positive coefficient suggests that having a waterfront view tends to be associated with higher prices.Having a water front increases the price of the house by 795,274.30 dollars.

grade_11 Excellent (2.684861e+05), grade_12 Luxury (7.451221e+05), grade_13 Mansion (2.003131e+06): These coefficients represent the estimated price differences for properties with different grades compared to a reference category (possibly grade_1 or another reference grade). Higher grade levels are associated with higher prices.

grade_3 Poor to grade_9 Better: These coefficients represent the estimated price differences for properties with different grade levels compared to the reference category (grade_1 or another reference grade). Negative coefficients (e.g., grade_3 Poor) suggest lower prices compared to the reference category, while positive coefficients (e.g., grade_9 Better) suggest higher prices.

Overall, these coefficients provide insight into the relationship between each predictor variable and the target variable (price) in the multiple linear regression model. They indicate the estimated change in price associated with a unit change in each predictor, assuming other variables are held constant. The signs and magnitudes of the coefficients help identify the direction and strength of these associations.

#####CONCLUSION

A larger living space in the home tends to be associated with higher prices.Buyers typically consider more square footage as desirable and are willing to pay a premium for it.Thus a larger living space is an essentisl requirement

Having a waterfront view tends to be associated with higher prices.

Higher grade levels in relation to design and construction are associated with higher prices.
