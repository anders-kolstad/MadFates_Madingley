--- 
title: "Runniging the Madingley Model with Norwegian data"
author: "Anders L. Kolstad"
date: "2021-12-14"
site: "bookdown::bookdown_site"
output:
  bookdown::gitbook: default
documentclass: book
link-citations: yes
---

# Introduction

This work is part of the MadFates project, run by Joachim Töpper. The goal is to learn bit about the Madinley model and its potential for modelling biomass distributions across trophic levels in Norwegian boreal ecosystem. Perhaps limited to forests.

This page is hosted in GitHub and produced using bookdown.

## Some useful links

Paper on the [R package](https://onlinelibrary.wiley.com/doi/full/10.1111/geb.13354)

Paper on the [model itself](https://journals.plos.org/plosbiology/article?id=10.1371/journal.pbio.1001841)

### Examples of use

[Removing carnivores](https://onlinelibrary.wiley.com/doi/10.1111/ecog.05191)

[Land-use change](https://www.nature.com/articles/s41598-020-70960-9)


## Terms and definitions

- Cohorts - Organisms with similar functional roles are grouped into cohorts which are treated as sinle entities in the model to reduce computational requirements.

- Stock - autotrofic biomass is treated as a single entity (stock).

- Model initialisation - After loading input data the model is run once without a year parameter. Not sure why exactly, or what the output is. 

- Spin-up phase - The model needs to run for 100-1000 simulated years without any user modifications to allow the ecosystem componets to reach a stable state. 





