# Flow charts

Creating flow charts in Stata is now easy! Given an Excel spreadsheet with columns A, B, C, and D titled “logic”, “var”, “stat” and “value”, respectively, `statflow` replaces the “value” column with the requested statistic for the observations in the dataset that fit the condition expressed in “logic”. This allows for the creation of dynamically updating custom tables and flowcharts. Here's an example:

![Making flowcharts with Stata](/img/flowchart.png)

```stata
  // Set up a flowchart:
    statflow template using "/path/to/file.xlsx" , [replace]

  // Fill it out, then get all the requested statistics:
    statflow using "/path/to/file.xlsx" [if] [in]
```

`statflow` is coming soon to [SSC](https://ideas.repec.org/) and is open for development on [GitHub](https://github.com/bbdaniels/statflow). Submit bugs and feature requests [here](https://github.com/bbdaniels/statflow/issues). If you like `statflow`, be sure to visit my [homepage](http://bbdaniels.github.io) and [Stata boilerplate code](https://gist.github.com/bbdaniels/a3c9f9416f1d16d6f3c6e8cf371f1d89).
