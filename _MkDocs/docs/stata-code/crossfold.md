# Performing k-fold cross-validation

## Description

`crossfold` performs k-fold cross-validation on a specified model in order to evaluate a model's ability to fit out-of-sample data.

## Example
```
. ssc install crossfold
. sysuse nlsw88 , clear
. crossfold reg wage union

             |      RMSE
-------------+-----------
        est1 |  4.171849
        est2 |  4.105884
        est3 |  4.038483
        est4 |  4.151482
        est5 |  4.171727
```

This procedure splits the data randomly into k partitions, then for each partition it fits the specified model using the other k-1 groups and uses the resulting parameters to
predict the dependent variable in the unused group.

Finally, `crossfold` reports a measure of goodness-of-fit from each attempt. The default evaluation metric is root mean squared error (RMSE).

## Syntax
```stata
crossfold model [model_if] [model_in] [model_weight],
        [eif()] [ein()] [eweight(varname)]
        [stub(string)] [k(value)] [loud]
        [mae] [r2]
        [model_options]
```
```
Options               Description
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
eif; ein              Error evaluation if and in specifications place restrictions on the out-of-sample set that should be fit. Modelling if and in restrictions should be
                        specified with the model.
eweight               Weighting for error evaluation purposes. Model weights, identical or not, should be specified after the model.
stub()                Specifies a stub name for naming estimation results and for the results matrix. The default is est.
k()                   Specifies a number of folds to carry out. The default is 5, and k cannot exceed 300 or the number of observations.
loud                  Displays each model as it is fit.
mae                   Calculates mean absolute errors (MAE) instead of RMSE.
r2                    Calculates psuedo-R-squared (the square of the correlation coefficient of the predicted and actual values of the dependent variable) instead of RMSE.
model_options         Modelling command options (such as fe for xtreg).
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
```

`crossfold` is available on [SSC](https://ideas.repec.org/c/boc/bocode/s457426.html) and is open for development on [GitHub](https://github.com/bbdaniels/crossfold). Submit bugs and feature requests [here](https://github.com/bbdaniels/crossfold/issues). If you like `crossfold`, be sure to visit my [homepage](http://bbdaniels.github.io) and [Stata boilerplate code](https://gist.github.com/bbdaniels/a3c9f9416f1d16d6f3c6e8cf371f1d89).
