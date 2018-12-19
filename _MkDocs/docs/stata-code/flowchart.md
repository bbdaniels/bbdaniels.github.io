# Flow charts

Creating flow charts in Stata is now easy! Given an Excel spreadsheet with columns A, B, C, and D titled “logic”, “var”, “stat” and “value”, respectively, `flowchart` replaces the “value” column with the requested statistic for the observations in the dataset that fit the condition expressed in “logic”. This allows for the creation of dynamically updating custom tables and flowcharts. Here's an example:

![Making QR codes with Stata](/img/flowchart.png)

```stata
flowchart using "flowchart.xlsx"
```

`knapsack` is coming soon to [SSC](https://ideas.repec.org/) and is open for development on [GitHub](https://github.com/bbdaniels/flowchart). Submit bugs and feature requests [here](https://github.com/bbdaniels/flowchart/issues). If you like `flowchart`, be sure to visit my [homepage](http://bbdaniels.github.io) and [Stata boilerplate code](https://gist.github.com/bbdaniels/a3c9f9416f1d16d6f3c6e8cf371f1d89).
