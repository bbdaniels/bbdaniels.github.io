## Making bar graphs with standard error bars in Stata

Making graphs with confidence intervals in Stata is now easy! Here's an example using `betterbar`:

![Graphs with confidence intervals in Stata](/img/betterbar.png)

```stata
ssc install betterbar

global tw_opts ///
	title(, justification(left) color(black) span pos(11)) ///
	graphregion(color(white) lc(white) lw(med)) bgcolor(white) ///
	ylab(,angle(0) nogrid) xtit(,placement(left) justification(left)) ///
	yscale(noline) xscale(noline) legend(region(lc(none) fc(none)))

sysuse auto.dta , clear

betterbarci headroom trunk mpg , over(foreign) ${tw_opts}
```

`betterbar` is available on [SSC](https://ideas.repec.org/c/boc/bocode/s458560.html) and is open for development on [GitHub](https://github.com/bbdaniels/betterbar). Submit bugs and feature requests [here](https://github.com/bbdaniels/betterbar/issues). If you like `betterbar`, be sure to visit my [homepage](http://bbdaniels.github.io) and [Stata boilerplate code](https://gist.github.com/bbdaniels/a3c9f9416f1d16d6f3c6e8cf371f1d89).
