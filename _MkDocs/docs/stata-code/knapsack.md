# Solving knapsack problems

Stata can now solve constrained optimization problems of the "knapsack" variety! Given a budget constraint and a dataset of items with prices and values, `knapsack` will calculate the most valuable obtainable combination under the given budget, and returns those items and their total value. Here's an example:

```stata
. sysuse auto.dta, clear
(1978 Automobile Data)

. keep mpg price
. rename (mpg price)(cost value)

. knapsack 500, p(cost) v(value) gen(chosen)
(74 missing values generated)
Maximum Total Price = 253853

. di "`r(max)'"
253853

. table chosen , c(sum cost sum value)
----------------------------------
   chosen |  sum(cost)  sum(value)
----------+-----------------------
        0 |       1076      202376
        1 |        500      253853
----------------------------------
```

`knapsack` is coming soon to [SSC](https://ideas.repec.org/) and is open for development on [GitHub](https://github.com/bbdaniels/knapsack). Submit bugs and feature requests [here](https://github.com/bbdaniels/knapsack/issues). If you like `knapsack`, be sure to visit my [homepage](http://bbdaniels.github.io) and [Stata boilerplate code](https://gist.github.com/bbdaniels/a3c9f9416f1d16d6f3c6e8cf371f1d89).
