# 8 - Stats Refresher

## Types of Variables: Categorical vs Numeric

- Categorical
  - Describe quality or characteristic of the variable
  - Nominal - Cannot be organized logically
    - Gender - Male, Female
    - Color - Red, Green, Black
  - Ordinal - Can be organized logically
    - Size - Small, Medium, Large
    - Grades - A, B, C, etc.
- Numeric
  - Discrete - Whole numbers (how many units, no fractions)
    - 1, 2, 3, etc. businesses
    - 568 people
  - Continuous - How many, with fractions.
    - Age
    - Height

## Regressions

In statistics, regression analysis is a statistical process for estimating the relationships amoung variables. ...
The focus is on the relationship between a dependent variable and one or more independent varaibles -- Wikipedia

- Linear
  - Simple Linear Regression
    - y = b<sub>0</sub> + b<sub>1</sub> * x<sub>1</sub>
    - Sloped line on an XY Axis
      - y: Dependent Variable (what you're trying to explain)
      - x<sub>1</sub>: Independent variable (causes dependent variable to change)
      - b<sub>1</sub>: Coefficient (how a unit change in x will change y) (slope of line)
      - b<sub>0</sub>: Constant (Y intercept value)
  - Multiple Linear Regression
    - Same as Simple Linear Regression, but many variables
    - y = b<sub>0</sub> + b<sub>1</sub> + x<sub>1</sub> + b<sub>2</sub> * x<sub>2</sub> + ... + b<sub>n</sub> * x<sub>n</sub>
- Logistic
  - Simple Logistic Regression (rarely used)
  - Multiple Logistic Regression

### Simple Linear Regression

- Salary ($) - Y Axis
- Experience - X Axis
- Line that best fits the data
- y = b<sub>0</sub> + b<sub>1</sub> * x<sub>1</sub> => Salaray = b<sub>0</sub> + b<sub>1</sub> * Experience
  - b<sub>0</sub>: Constant, X intercept
    - With 0 experience, person will make $30k
  - b<sub>1</sub>: Slope of the line
    - Someone moves from 4 to 5 years of Experience
    - Person will get an extra $10k
    - Steeper slope, experience yields higher salaries

## Ordinary Least Squares

- Linear Regression line should indicate where a person falls on the Salaray/Experience Chart
- y<sub>î</sub>: the point on the linear regression (modeled value)
- y<sub>i</sub>: the point of actual data
- y<sub>i</sub> - y<sub>î</sub>: difference between observed and modeled value
- SUM (y<sub>i</sub> - y<sub>î</sub>)<sup>2</sup> = min sum of squares

## R Squared
- Sum of Squares of Residuals
  - SS<sub>res</sub> = SUM (y<sub>i</sub> - y<sub>î</sub>)<sup>2</sup>
- Total Sum of Squares
  - SS<sub>tot</sub> = SUM (y<sub>i</sub> - y<sub>avg</sub>)<sup>2</sup>
- R<sup>2</sup> = 1 - SS<sub>res</sub> / SS<sub>tot</sub>
  - How good is a line against the average
  - Try to minimize SS<sub>res</sub>
  - The closer R<sup>2</sup> to 1, the better
    - R<sup>2</sup> can be negative, but indicates a broken model

## Adjusted R Squared

- R<sup>2</sup> - Goodness of fit (greater is better)
- Problem:
  - Add a third variable to see if the model fits even better
  - y = b<sub>0</sub> + b<sub>1</sub> + x<sub>1</sub> + b<sub>2</sub> * x<sub>2</sub> + b<sub>3</sub> * x<sub>3</sub>
  - Did R<sup>2</sup> increase, or decrease
    - R<sup>2</sup> will never decrease!!!!
    - SS<sub>res</sub> will change, but SS<sub>tot</sub> won't.
- Adj R<sup>2</sup> = 1 - (1 - R<sup>2</sup>)((n - 1)/(n - p - 1))
  - p number of regressors
  - n sample size
  