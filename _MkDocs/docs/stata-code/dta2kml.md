# Outputting a KML file from a dataset

Making KML files in Stata is now easy! Here's an example using `dta2kml`:

![Outputting a KML file from a Stata dataset](/img/dta2kml.jpg)

```stata
ssc install dta2kml

clear
	set obs 100
	gen lat = rnormal() +38
	gen lon = rnormal() -77

dta2kml using "demo.kml" , lat(lat) lon(lon) replace
```

## Syntax

```stata
dta2kml using filename [if] [in], [replace]
        latitude(varname) longitude(varname) [altitude(varname)]
        [lines(group_var index_var)] [point_options]


    Options               Description
    ------------------------------------------------------------------------
    Line Options

    lines()               Specify the grouping variable (unique for each
                            line) and the index variable, ranging from 1 to
                            n consecutively for each element. If lines() is
                            specified only this type of data can be used.

    Point Options

    folders()             Indicates a variable containing folder names.
    names()               Indicates a variable containing placemark names.
    icons()               Indicates a variable containing the full URLs of
                            the desired icons from the libraries located at
                            http://kml4earth.appspot.com/icons.html. If this
                            option is not specified, all placemarks display
                            the default icon.
    descriptions()        Indicates a variable containing descriptions to
                            attach to the placemarks.
    ------------------------------------------------------------------------
```

`dta2kml` is available on [SSC](https://ideas.repec.org/c/boc/bocode/s457748.html) and is open for development on [GitHub](https://github.com/bbdaniels/dta2kml). Submit bugs and feature requests [here](https://github.com/bbdaniels/dta2kml/issues). If you like `dta2kml`, be sure to visit my [homepage](http://bbdaniels.github.io) and [Stata boilerplate code](https://gist.github.com/bbdaniels/a3c9f9416f1d16d6f3c6e8cf371f1d89).
