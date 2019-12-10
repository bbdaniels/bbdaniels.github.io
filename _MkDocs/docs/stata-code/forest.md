# Treatment effect graphs

Visualizing treatment effects on multiple outcomes with Stata is now easy! Here's an example using `forest`:

![Visualizing treatment effects on multiple outcomes with Stata](/img/forest.png)

```stata
sysuse auto.dta , clear
forest reg ///
  (mpg headroom trunk) ///
  (rep78 gear_ratio turn) ///
  , t(foreign) bh
```

`forest` visualizes results from multiple regressions on a single independent variable.  The resulting "forest" chart
shows the effect of a single treatment variable of interest on a set of independent variables.  It can display raw
coefficients, standardized effect sizes (Cohen's d), or odds ratios (from logistic regressions).  It can also make
Bonferroni corrections to the confidence intervals for multiple comparisons.

`forest` is available on [SSC](https://ideas.repec.org/c/boc/bocode/s458591.html) and is open for development on [GitHub](https://github.com/bbdaniels/forest). Submit bugs and feature requests [here](https://github.com/bbdaniels/forest/issues). If you like `forest`, be sure to visit my [homepage](http://bbdaniels.github.io) and [Stata boilerplate code](https://gist.github.com/bbdaniels/a3c9f9416f1d16d6f3c6e8cf371f1d89).
