# Unique IDs

Making best-practice unique IDs in Stata is now easy! Here's an example using `makeid`:

```stata
. sysuse auto.dta , clear
(1978 Automobile Data)

. makeid foreign make , gen(uniqueid) project(Demo)
(data now sorted by foreign make)
(data now sorted by uniqueid)

. de uniqueid

              storage   display    value
variable name   type    format     label      variable label
----------------------------------------------------------------------
uniqueid        str4    %9s                   Demo ID: foreign + make

. list foreign make uniqueid in 1/5

     +-------------------------------------+
     |  foreign   make            uniqueid |
     |-------------------------------------|
  1. | Domestic   AMC Concord         D101 |
  2. | Domestic   AMC Pacer           D102 |
  3. | Domestic   AMC Spirit          D103 |
  4. | Domestic   Buick Century       D104 |
  5. | Domestic   Buick Electra       D105 |
     +-------------------------------------+

. list foreign make uniqueid in 53/57

     +---------------------------------+
     | foreign   make         uniqueid |
     |---------------------------------|
 53. | Foreign   Audi 5000        D201 |
 54. | Foreign   Audi Fox         D202 |
 55. | Foreign   BMW 320i         D203 |
 56. | Foreign   Datsun 200       D204 |
 57. | Foreign   Datsun 210       D205 |
     +---------------------------------+
```

`makeid` creates a unique ID for every observation in the dataset, based on strata-type variables.

For example, given a variable list such as _country state district name_, a unique ID is returned for every observation such that:

1. Country code in the ID is fully unique
2. State code in the ID is unique within country
3. District code in the ID is unique within country and state
4. Each name has a unique ID within country, state, and district.

`makeid` prefixes each ID with the first letter of the project name, as a best practice to prevent against automatic conversion to numbers in Excel for example.


`makeid` is coming soon to [SSC](https://ideas.repec.org/) and is open for development on [GitHub](https://github.com/bbdaniels/makeid). Submit bugs and feature requests [here](https://github.com/bbdaniels/makeid/issues). If you like `makeid`, be sure to visit my [homepage](http://bbdaniels.github.io) and [Stata boilerplate code](https://gist.github.com/bbdaniels/a3c9f9416f1d16d6f3c6e8cf371f1d89).
