Lab 03 - Nobel laureates
================
Sophie Boyd
1-30-26

### Load packages and data

``` r
library(tidyverse) 
```

``` r
nobel <- read_csv("data/nobel.csv")
```

## Exercises

### Exercise 1

``` r
view(nobel)
```

There are 935 observations of 26 variables. Each row represents one
Nobel prize.

### Exercise 2

``` r
nobel_copy <- nobel

nobel_living <- nobel_copy %>% filter(
  is.na(died_date),
  !is.na(country),
  gender != "org"
  )

View(nobel_living)
```

Down to 228 observations after filtering for laureates who are still
alive, have available information on country, and who are people (not
organizations)

### Exercise 3

Remove this text, and add your answer for Exercise 1 here. Add code
chunks as needed. Don’t forget to label your code chunk. Do not use
spaces in code chunk labels.

### Exercise 4

…

### Exercise 5

…

### Exercise 6

…
