--- 
title: "Running the Madingley Model with Norwegian data"
author: "Anders L. Kolstad"
date: "2022-08-10"
site: "bookdown::bookdown_site"
output:
  bookdown::gitbook: default
documentclass: book
link-citations: yes
---

# Introduction

This work is part of the MadFates project, run by Joachim Töpper. The goal is to learn bit about the Madingley model and its potential for modeling biomass distributions across trophic levels in Norwegian boreal ecosystem. Perhaps limited to forests.

* How can we validate the model?
* What can we use the model for?

This page is hosted in GitHub and produced using bookdown.

## Some useful links

Paper on the [R package](https://onlinelibrary.wiley.com/doi/full/10.1111/geb.13354)

Paper on the [model itself](https://journals.plos.org/plosbiology/article?id=10.1371/journal.pbio.1001841)

### Examples of use

[Removing carnivores](https://onlinelibrary.wiley.com/doi/10.1111/ecog.05191)

[Land-use change](https://www.nature.com/articles/s41598-020-70960-9)


## Terms and definitions

- `Function group` - Madingley divides animal species into 9 functional groups, confusingly numbered 0-8.

    + 0 = Endothermic herbivores (e.g. moose)
    + 1 = Endothermic carnivores (e.g. wolves)
    + 2 = Endothermic omnivores (e.g. bears)
    + 3 = Ectothermic semelparous herbivores (e.g. grasshoppers)
    + 4 = Ectothermic semelparous carnivores (e.g. ants)
    + 5 = Ectothermic semelparous omnivores (e.g. insects, snails)
    + 6 = Ectothermic iteroparous herbivores (e.g. ?)
    + 7 = Ectothermic iteroparous carnivores (e.g. snakes)
    + 8 = Ectothermic iteroparous omnivores (e.g. ?)
    
- `Cohorts` - Although an individual based model, this just means that the model represents interactions between individuals, and not that it models each of these interactions uniquely. To reduce computational time, individuals are grouped into cohorts if they:

    + belong to the same function group
    + exists inthe same grid cell
    + have identical continuous traits (e.g. body mass)
    
Note that a cohort does not care about species identities. The user can set the number of cohorts. The default is 500 and the maximum in 1000. This is per cell.

- `Dispersion` - cohorts can disperse between grid cells 

- `Stocks` - autotrophic biomass is is divided between deciduous and evergreen biomass and treated as a single entity (stock).

- `Model initialisation` - After loading input data the model is run once without a _year_ parameter. Not sure why exactly, or what the output is. 

- `Spin-up phase` - The model needs to run for 100-1000 simulated years without any user modifications to allow the ecosystem components to reach a stable state. 

- `HANPP` - human appropriation of net primary productivity. The variable spans from zero (or actually with some points <0 which I don't understand how to interpret) and 1200. I'm not sure what the units are, but probably they are the same as for the autotrophic biomass. In [case study 2](https://github.com/MadingleyR/MadingleyR/blob/master/CaseStudies/CASESTUDY2.md) they simply set the value to a uniform value between zero and one in this way:

```r
sptl_inp$hanpp[] = fractional_veg_production[i]
```

and set 'apply_hanpp =1' which reduces NPP in fractions provided in the hanpp spatial input raster.
The example HANPP input data is from year 2005.


```r
library(MadingleyR)
library(raster)
sptl_inp = madingley_inputs("spatial inputs")
```

```
## Warning: package 'rgdal' was built under R version 4.1.3
```

```
## Reading default input rasters from:  C:/Users/anders.kolstad/Documents/R/R-4.1.2/library/MadingleyR/spatial_input_rasters.............
```

```r
raster::plot(sptl_inp$hanpp, main = "HANPP anno 2005")
```

<img src="index_files/figure-html/unnamed-chunk-2-1.png" width="480" />


