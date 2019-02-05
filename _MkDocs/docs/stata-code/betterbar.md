# Bar graphs with CIs

Making graphs with confidence intervals in Stata is now easy! Here's an example using `betterbar`:

![Graphs with confidence intervals in Stata](/img/betterbar.png)

```stata
ssc install betterbar
sysuse auto.dta , clear
betterbarci ///
  headroom trunk mpg ///
  , over(foreign) legend(on)
```

`betterbar` is available on [SSC](https://ideas.repec.org/c/boc/bocode/s458560.html) and is open for development on [GitHub](https://github.com/bbdaniels/betterbar). Submit bugs and feature requests [here](https://github.com/bbdaniels/betterbar/issues). If you like `betterbar`, be sure to visit my [homepage](http://bbdaniels.github.io). Thanks to Gray Kimbrough for the [Uncluttered Stata Graph Theme](https://graykimbrough.github.io/uncluttered-stata-graphs/).
