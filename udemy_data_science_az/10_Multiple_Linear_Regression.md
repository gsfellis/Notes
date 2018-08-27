# Multiple Linear Regression

## Caveats

Assumptions of a Linear Regression:

1. Linearity
2. Homoscedasticity
3. Multivariate normality
4. Independence of errors
5. Lack of multicollinearity

Our goal:

- Geodemographic Segmentation MOdel
- Requires Logistic Regression
- Different Assumptions

## Dummy Variables

| Profit | R&D Spend | Admin | Market | State |
|---|---|---|---|---|
| 165349.2 | 136897.8 | 471784.1 | 192261.83 | New York |
| 162597.7 | 151377.59 | 443898.53 | 191792.06 | California |
| 153441.51 | 101145.55 | 407934.54 | 191050.39 | California |
| 144372.41 | 118671.85 | 383199.62 | 182901.99 | New York |
| 142107.34 | 91391.77 | 366168.42 | 166187.94 |California |
| y = b<sub>0</sub> | b<sub>1</sub> * x<sub>1</sub> | b<sub>2</sub> * x<sub>2</sub> | b<sub>3</sub> * x<sub>3</sub> | ??? |

- What do we do for the state? (Categorical predictor)
  - Need to create Dummy Variables

| Profit | R&D Spend | Admin | Market | State | New York | California |
|---|---|---|---|---|---|---|---|
| 165349.2 | 136897.8 | 471784.1 | 192261.83 | New York | 1 | 0 |
| 162597.7 | 151377.59 | 443898.53 | 191792.06 | California | 0 | 1 |
| 153441.51 | 101145.55 | 407934.54 | 191050.39 | California | 0 | 1 |
| 144372.41 | 118671.85 | 383199.62 | 182901.99 | New York | 1 | 0 |
| 142107.34 | 91391.77 | 366168.42 | 166187.94 |California | 0 | 1 |
| y = b<sub>0</sub> | + b<sub>1</sub> * x<sub>1</sub> | + b<sub>2</sub> * x<sub>2</sub> | + b<sub>3</sub> * x<sub>3</sub> | | + b<sub>4</sub> * D1 | |

- Add new columns for each categorical value
  - New York, California are Dummy Variable Columns
- Fill in each with a 1 in their respective columns
- Never include all dummy variables
  - Use only the New York column, in this case
  - Works like switches, 1 is on, 0 is off

### Dummy Variable Trap

- What happens if we include all dummy variables
  - +b<sub>5</sub> * D<sub>2</sub>
  - !!!!! D<sub>2</sub> = 1 - D<sub>1</sub> !!!!!
    - Multicolinearity - 1 or several variables predict another
    - Effects from D<sub>1</sub> can't be distinguished from D<sub>2</sub>
  - Cannot include the constant and all Dummy Variables at a time
  - Always omit one dummy variable
    - Must be done for each Dummy Variable Sets

## Building a Model

Which predictors should we keep or get rid of.

Why?

1. Garbage in, Garbage Out
2. Need to explain the variables

5 methods of building models:

1. All-in
   - Prior knowledge
   - You have to
   - Preparing for Backward Elimination
2. Backward Elimination (Stepwise Regression)
   1. Select a significance level to stay in the model (e.g. SL = 0.05)
   2. Fit the full model with all possible predictors
   3. Consider the predictor with the _highest_ P-value.
      - If P > SL, go to STEP 4, Otherwise go to STEP 6
   4. Remove the predictor
   5. Fit model without this variable
      - Must rebuild the model to see how other variables are affected
      - Return to STEP 3
   6. Model is ready
3. Forward Selection (Stepwise Regression)
   1. Select a significance level to ender the model (e.g. SL = 0.05)
   2. Fit all simple regression models **y ~ x<sub>n</sub>**. Select the one with the lowst P-Value
   3. Keep this variable and fit all possible models with one extra predictor added to the one(s) you already have
   4. Consider the predictor with the _lowest_ P-value.
      - If P < SL, go to STEP 3, otherwise go to STEP 5
   5. Keep the _previous_ model
4. Bidirectional Elimination (Sometimes called "Stepwise Regression")
   1. Select a significance level to enter and to stay in the model (SLENTER = 0.05, SLSTAY = 0.05)
   2. Perform the next step of Forward Selection (new variables P < SLENTER)
   3. Perform **ALL** steps of Backward Elmination (old variables must have P < SLSTAY)
   4. No new variables can enter and no old variables can exit
   5. Model is ready
5. Score Comparison (All Possible Models)
   1. Select a criterion of goodness of fit (e.g. Akaike criterion)
   2. Construct All Possible Regression Models: 2<sup>N</sup>-1 total combinations
   3. Select the one with the best criterion
      - Example: 10 columns means 1,023 models!
   4. Model is ready
