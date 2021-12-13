# Installation

Madingley is written in C++, but an R version is also available. Although a little bit less flexible perhaps, it should be more than sufficient four this project. And much more familiar.





```r
library(devtools)
install_github('MadingleyR/MadingleyR', subdir='Package', build_vignettes = F)
```

I could not get the vignetts to build. 


```r
vignette(package ="MadingleyR") 
```

```
## no vignettes found
```
They can, however, be view [here](https://github.com/MadingleyR/MadingleyR).


```r
MadingleyR::madingley_version()
```
This line also did not work. The verdsion seems to be 1.0.2. Source version, I don't know.



