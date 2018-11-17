<!-- README.md is generated from README.Rmd. Please edit that file -->



# stargazer

A Clone of
[stargazer 5.2.2](https://cran.r-project.org/web/packages/stargazer/index.html) that
properly prints the dependent variable from a list of  `felm`
models. Installing stargazer from this repo yields the output from a list of `felm` models:


```r
library(lfe); library(stargazer)
data(mtcars)
mtcars$cyl <- as.factor(mtcars$cyl)

## -- Current Implementation -- ##
f <- list(
  mpg ~ wt | 0 | 0 | 0,
  mpg ~ wt + hp | 0 | 0 | 0,
  disp ~ wt + hp | 0 | 0 | 0
)
mods <- lapply(f, felm, data = mtcars)
stargazer(mods, type = "text")
#> 
#> ====================================================================
#>                                   Dependent variable:               
#>                     ------------------------------------------------
#>                                   mpg                     disp      
#>                           (1)             (2)             (3)       
#> --------------------------------------------------------------------
#> wt                     -5.344***       -3.878***       82.113***    
#>                         (0.559)         (0.633)         (11.552)    
#>                                                                     
#> hp                                     -0.032***        0.658***    
#>                                         (0.009)         (0.165)     
#>                                                                     
#> Constant               37.285***       37.227***      -129.951***   
#>                         (1.878)         (1.599)         (29.189)    
#>                                                                     
#> --------------------------------------------------------------------
#> Observations              32              32               32       
#> R2                       0.753           0.827           0.863      
#> Adjusted R2              0.745           0.815           0.854      
#> Residual Std. Error 3.046 (df = 30) 2.593 (df = 29) 47.348 (df = 29)
#> ====================================================================
#> Note:                                    *p<0.1; **p<0.05; ***p<0.01
```


## Installation

You can install stargazer from github with:


```r
# install.packages("devtools")
devtools::install_github("ChandlerLutz/stargazer")
```
