
# compaRe

<!-- badges: start -->
<!-- badges: end -->

The goal of `compaRe` package is to compare two versions of the same data set and produce the differences between the two.

## Installation

You can install the development version of compare as below:

``` r
library(devtools)
install_github("Fahim-Ahmad/compaRe")
```

## Usage
``` r
library(compaRe)
compare_df(df1, df2, unique_id_df1, unique_id_df2, compare_all = TRUE)
```

## Arguments
  `df1` Old version of the dataset

  `df2` Latest version of the dataset

  `unique_id_df1` unique identifier in df1

  `unique_id_df2` unique identifier in df2
  
  `compare_all` logical. `TRUE`: compare all columns/variables. `FALSE`: compare only shared columns/variable. 

## Example

``` r
library(compaRe)

mtcars_v1 <- mtcars_v2 <- mtcars
mtcars_v1$id <- mtcars_v2$id <- rownames(mtcars)

mtcars_v2$am[mtcars_v2$am == 1] <- 2
mtcars_v2$wt[mtcars_v2$wt > 100] <- 105
mtcars_v2$cyl[mtcars_v2$cyl == 8] <- 7
mtcars_v2 <- mtcars_v2[1:30, ]
mtcars_v2$rowid <- 1:nrow(mtcars_v2)

compare_df(df1 = mtcars_v1, df2 = mtcars_v2,
          unique_id_df1 = "id",
          unique_id_df2 = "id",
          compare_all = TRUE
          )
          
compare_df(df1 = mtcars_v1, df2 = mtcars_v2,
          unique_id_df1 = "id",
          unique_id_df2 = "id",
          compare_all = FALSE
          )
```

