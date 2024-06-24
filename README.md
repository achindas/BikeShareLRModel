# Bike Share Demand Forecasting Case Study - Multiple Linear Regression

## Table of Contents
* [Linear Regression Overview](#linear-regression-overview)
* [Problem Statement](#problem-statement)
* [Technologies Used](#technologies-used)
* [Approach for MLR](#approach-for-mlr)
* [Regression Outcome](#regression-outcome)
* [Conclusion](#conclusion)
* [Acknowledgements](#acknowledgements)

## Linear Regression Overview

**Linear Regression** is one of the most commonly used algorithms in machine learning and statistics used in industry. It models the relationship between a dependent variable (target) and one or more independent variables (predictors) by fitting a linear equation to the observed data. Here is how the simple LR model is represented:

$$ y\ =\ \beta_0+\ \beta_1\ x\ +\ \epsilon $$

where:
- $y$ is the dependent variable.
- $x$ is the independent variable.
- $\beta_0$ is the intercept.
- $\beta_1$ is the slope of the line.
- $\epsilon$ is the error term, representing the difference between the observed and predicted values.

In multiple linear regression (MLR), the model includes multiple independent variables:

$$ y = \beta_0 + \beta_1 x_1 + \beta_2 x_2 + \cdots + \beta_p x_p + \epsilon $$

where $x_1, x_2, \ldots, x_p$ are the independent variables.

The coefficients $\beta$ can be calculated using the Normal Equation:

$$ \beta = (X^T X)^{-1} X^T y $$

Here, $X^T$ is the transpose of the design matrix $X$, containing the independent variables, and $y$ is the vector of observed values.

MLR has been utilized in this case study in a step-by-step manner to understand, analyse, transform and model the data provided for the analysis. The approach described here represent the practical process utilised in industry to predict numerical target parameters for business.


## Problem Statement

A US bike-sharing provider **BoomBikes** wants to come up with a mindful business plan to be able to accelerate its revenue as soon as the ongoing lockdown comes to an end, and the economy restores to a healthy state. BoomBikes aspires to understand the demand for shared bikes among the people to prepare themselves to cater to the people's needs once the situation gets better all around and stand out from other service providers and make huge profits.

Specifically, they want to understand the factors affecting the demand for these shared bikes in the American market. The company wants to know:

* Which variables are significant in predicting the demand for shared bikes
* How well those variables describe the bike demands

Based on various meteorological surveys and people's styles, the service provider firm has gathered a large dataset on daily bike demands across the American market based on some factors. 


**This exercise aims to model the demand for shared bikes** with the given independent variables. It will be used by the management,
* to understand how exactly the demands vary with different features
* to change the business strategy to meet the demand levels and meet the customer's expectations.
* to understand the demand dynamics of a new market


## Technologies Used

Python Jupyter Notebook with Numpy, Pandas, Matplotlib and Seaborn libraries are used to prepare, analyse and visualise data. The following MLR specific libraries have been used in the case study:

- scikit-learn
- statsmodels


## Approach for MLR

A ten-step approach is used across Analyse, Build and Evaluate phases for this modelling exercise:

* <span style="font-size: 18px;">Analyse Data</span>
    1. Import & Understand Data
    2. Handle Missing and Bad Quality Data
    3. Perform Exploratory Data Analysis
    4. Handle & Transform Categorical Variables
    5. Derive New Metrics & Analyse

* <span style="font-size: 18px;">Build Model</span>

    6. Build Initial Model & Analyse Performance
    7. Finetune Model by Adding Features

* <span style="font-size: 18px;">Evaluate Model</span>

    8. Analyse Residuals and Validate Model Assumptions
    9. Perform Prediction and Evaluate Final Model
    10. Explain Final Model for Business Use

Some distinguishing processes in this approach include,

- Conversion of multi-level categorical variables (variables having more than two unique categorical values) to multiple dummy variables with 0 & 1 values

- Split the available data into `Training` (contains typically 70% of data) and `Test` data sets

- Scale the training data set using appropriate `Scaler` to bring all the independent variables to same range

- Build the initial model with most appropriate variable(s) using training data set and assess the model performance parameters like `R-squared` and `Adjusted R-squared`

- Keep enhancing the model performance by adding more variables while monitoring the relevance of the variables (using `p-values`) and the model itself (using `Prob (F-statistic)`)

- If there are many variables, apply automated `Recursive Feature Elimination (RFE)` technique to narrow down on desired features faster

- Further fine-tune the model by reducing collinearity within the independent variables using `Variance Inflation Factor (VIF)` computation and eliminating collinear variables

- On achieving reasonable `R-squared` score, perform residual analysis to validate the model assumptions of `Linearity`, `Independence`, `Homoscedasticity` and `Normality`.

- Perform prediction using `Test` data set by scaling it using previously established `Scaler`

- Evaluate if the `R-squared` score is still about the same and the model assumptions are still valid on `test` data set also

- Finally explain the model in business terms for easy comprehension of Business Users

## Regression Outcome
Equation of our best fitted line is:

$ cnt = 0.220 + 0.235  \times  yr + 0.473 \times temp - 0.157 \times windspeed - 0.040 \times Jan - 0.047 \times Jul + 0.072 \times Sep - 0.045 \times Sun - 0.081 \times Cloudyday - 0.287 \times Wetday - 0.062 \times Spring + 0.044 \times Summer + 0.077 \times Winter $

There are **twelve** factors that determine the bike demands in the subject locality for a day in year:

* **Rental Year &uarr;** - As the year progresses, bike demand is expected to rise, because of increased awareness about the facility among the users

* **Temperature &uarr;** - As the temperature increases (in otherwise cold climate), bike demand will grow significantly

* **Wind Speed &darr;** - On days wither high wind speed, demand is expected to fall

* **Jan &darr;/ July &darr;/ Sep &uarr;** - Demand will slightly fall in Jan & July, but increase in Sep

* **Sun &darr;** - Sundays will see slightly less demand as the office-going users will be less

* **Cloudyday &darr;/ Wetday &darr;** - Demand will be less compared to Clearday on days with heavy cloud or light rain/ snow.

* **Spring &darr;/ Summer &uarr;/ Winter &uarr;** - Demand will fall slightly in Spring, but increase in Summer & Winter due to higher temperature

## Conclusion

Linear regression is a powerful and interpretable algorithm for modeling relationships between variables. By understanding its assumptions, fitting the model, and evaluating its performance, we can make informed decisions and predictions based on data.


## Acknowledgements

This case study has been developed as part of Post Graduate Diploma Program on Machine Learning and AI, offered jointly by Indian Institute of Information Technology, Bangalore (IIIT-B) and upGrad.