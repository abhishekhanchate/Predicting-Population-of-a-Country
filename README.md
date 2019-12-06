# Predicting-Population-of-a-Country

## Challenge: World Bank Data
This challenge is based on the World Bank Data, which aggregates the population of various countries, along with fertility rate and life expectancy, from 1960 to 2016. The goal of this activity is to explore a regression analysis method that performs both variable selection and regularization in order to enhance the prediction accuracy and limit the fragility of a statistical model.

## Method 1: Regularized Least Squares
The method of least squares is a standard approach in regression analysis to approximate the solution of overdetermined systems. This technique is used extensively in the context of data fitting; the best fit in the least-squares sense minimizes the sum of squared residuals. In the current context, a regularized version to the least squares solution is highly desirable. Ridge regression, or Tikhonov regularization, adds the constraint that the L2-norm of the parameter vector remains no greater than a given value. An alternative regularized version of least squares is LASSO (least absolute shrinkage and selection operator), which uses the constraint that the L1-norm of the parameter vector be no greater than a given value. The latter constraint, which we will focus on, favors sparsity in the solution.

## Method 2: Correlation
An alternate approach is to find the top predictors by using the correlation coefficients between the intended vector and all candidates. The vectors with the strongest correlation coefficients can then be selected as the restricted set of predictors.

## Data
As mentioned above, the data we are using is based on the World Bank Data. Specifically, we are using a cleaned up version of country_population.csv where incomplete rows have been removed and extraneous columns have been deleted. The intent is to use year 1960 to 1999 to train a least squares/correlation models and, subsequently, explore their prediction power for year 2001 to 2016. For a given country, the solution should be a population estimate based on a linear combination of (at most) four other countries. Mathematically, the population of country $C_0$ is estimated based on the population of four other countries, \begin{equation} \hat{C}_0(\text{year}) = \sum_i \alpha_i C_i(\text{year}) \end{equation} subject to $\| \boldsymbol{\alpha} \|_0 \leq 4$. For every country, the parameters $\boldsymbol{\alpha}$ must be derived based on populations from 1960 to 1999.

## Evaluation
The evaluation criterion is the average sum of squared residuals for populations from 2000 to 2016.

## File Descriptions
> population_training.csv – the training data in Kaggle format (40 x 213)
> population_testing.csv – the test data in Kaggle format (17 x 213)
> population_sample.csv – A sample Kaggle solution (17 x 213)
> population_prediction_Cor.csv – A predicton file for Correlation (17 x 213)
> population_prediction_Lasso.csv – A predicton file for LASSO (17 x 213)
> population_parameters_Cor.csv – A parameter file for Correlation (213 x 213)
> population_parameters_Cor.csv – A parameter file for LASSO (213 x 213)
