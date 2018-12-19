# Regression tables

`outwrite` reads multiple regressions saved with estimates store, consolidates them into a
single table, and exports the results to a .xlsx, .xls, .csv, or .tex file:

![Writing regression tables to common filetypes.](/img/outwrite.png)

Alternatively, as a programming command, it will accept a single matrix and print that; it
will also look for matrix_STARS and affix that number of stars to each cell.

## Syntax

```stata
  outwrite estimates_1 estimates_2 [...]
    using /path/to/output.[xlsx|xls|csv|tex] ,
    [replace stats() drop(varlist)]
    [tstat|pvalue] [format(format)]
    [sheet(sheetname [,replace]) modify]
    [rownames("list" "of" "names") colnames("list" "of" "names")]

  ------------------------------------------------------------------------------------------
    Options

      replace         Allows outwrite to overwrite the output file.
      stats()         Adds statistics from e() at the bottom of the table, such as N, r2,
                        or scalars added by estadd.
      drop(varlist)   Suppresses reporting of all variables in in varlist from the output.
                        This can be a factor variable list.
      tstat|pvalue    Reports T-statistics or P-values in regression table, instead of the
                        default standard errors.
      format(format)  Format the table values. By default this is %9.2f.
      sheet()         Place results in a target sheet if using .xlsx format.
      modify          Allows outwrite to modify the output file. Often required with
                        sheet() to work as expected.
      rownames()      Manually renames rows of output. By default, the rows are named to
                        reflect the variables in the estimation command.
      colnames()      Manually renames columns of output. By default, the columns are
                        named to reflect the saved equation names.
    --------------------------------------------------------------------------------------
    Note: if used to export a matrix, stats(), drop(), and tstat|pvalue will not be
    accepted.
```

## Example

```
  sysuse auto.dta, clear
    reg price i.foreign##c.mpg
    est sto reg1
    reg price i.foreign##c.mpg##i.rep78
    est sto reg2
    estadd scalar h = 4
    reg price i.rep78
    est sto reg3
    estadd scalar h = 2.5

  outwrite reg1 reg2 reg3 using "test.xlsx" ///
   , stats(N r2 h)  replace col("TEST" "(2)") drop(i.rep78) format(%9.3f)
```

## Acknowledgments

While the concept of `outwrite` is original, we borrowed core functionality from `xml_tab` by
Zurab Sajaia and Michael Lokshin, and many ideas from such programs as `estout` by Ben Jann,
`outreg` by John Luke Gallup, `outreg2` by Roy Wada, `modltbl` by John H. Tyler, `mktab` by Nicholas Winter, `outtex` by Antoine Terracol, and `est2tex` by Marc Muendler.

`outwrite` is coming soon to SSC and is open for development on [GitHub](https://github.com/bbdaniels/outwrite). Submit bugs and feature requests [here](https://github.com/bbdaniels/outwrite/issues). If you like `outwrite`, be sure to visit my [homepage](http://bbdaniels.github.io) and [Stata boilerplate code](https://gist.github.com/bbdaniels/a3c9f9416f1d16d6f3c6e8cf371f1d89).
