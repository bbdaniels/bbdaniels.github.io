# Treatment effect graphs

Visualizing treatment effects on multiple outcomes with Stata is now easy! Here's an example using `forest`:

![Visualizing treatment effects on multiple outcomes with Stata](/img/forest.png)

```stata
global tw_opts ///
	title(, justification(left) color(black) span pos(11)) ///
    graphregion(color(white) lc(white) lw(med)) bgcolor(white) ///
    ylab(,angle(0) nogrid) xtit(,placement(left) justification(left)) ///
    yscale(noline) xscale(noline) legend(region(lc(none) fc(none)))

sysuse auto.dta , clear
forest reg mpg headroom trunk = displacement , graph($tw_opts)
```

`forest` visualizes results from multiple regressions on a single independent variable.  The resulting "forest" chart
shows the effect of a single treatment variable of interest on a set of independent variables.  It can display raw
coefficients, standardized effect sizes (Cohen's d), or odds ratios (from logistic regressions).  It can also make
Bonferroni corrections to the confidence intervals for multiple comparisons.

## Syntax
```stata
  forest estimator depvars = treatment
    [if] [in] , [weight(weight)] [controls(varlist)]
    [graphopts(twoway_options)] [or|d]
    [bonferroni] [est_options]
```
```
    Syntax            Description
    -------------------------------------------------------------------------------------
      estimator       Indicates the estimation command to be utilized.
      depvars         List the left-hand-side variables.
      treatment       List the independent variable of interest.

      or|d            Request effect sizes as odds ratios (by exponentiating regression
                        coefficients where possible) or in terms of Cohen's d (by
                        standardizing the dependent variables). (Choose only one.)
      bonferroni      Request confidence intervals calculated with Bonferroni correction
                        for simultaneous comparisons.  This is calculated by adjusting
                        the significance level to (100-5/(number of regressions)).

      weight()        Specify weights.
      controls()      Specify controls.
      graphopts()     Set any desired options for the graph.

      est_options     Specify any options needed for the estimator.
    -------------------------------------------------------------------------------------
```


`forest` is available on [SSC](https://ideas.repec.org/c/boc/bocode/s458591.html) and is open for development on [GitHub](https://github.com/bbdaniels/forest). Submit bugs and feature requests [here](https://github.com/bbdaniels/forest/issues). If you like `forest`, be sure to visit my [homepage](http://bbdaniels.github.io) and [Stata boilerplate code](https://gist.github.com/bbdaniels/a3c9f9416f1d16d6f3c6e8cf371f1d89).
