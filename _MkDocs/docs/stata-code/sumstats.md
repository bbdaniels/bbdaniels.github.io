# Summary statistics tables

Making tables of summary statistics with Stata is now easy! Here's an example using `sumstats`:

![Making tables of summary statistics with Stata](/img/sumstats.png)

```stata
sysuse auto.dta , clear
sumstats  ///
  (price mpg if foreign == 0) ///
  (price displacement length if foreign == 1) ///
  using "test.xlsx" , replace stats(mean sd)
```

`sumstats` is coming soon to [SSC](https://ideas.repec.org/) and is open for development on [GitHub](https://github.com/bbdaniels/sumstats). Submit bugs and feature requests [here](https://github.com/bbdaniels/sumstats/issues). If you like `sumstats`, be sure to visit my [homepage](http://bbdaniels.github.io) and [Stata boilerplate code](https://gist.github.com/bbdaniels/a3c9f9416f1d16d6f3c6e8cf371f1d89).
