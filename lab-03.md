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

``` r
nobel_living <- nobel_living %>%
  mutate(
    country_us = if_else(country == "USA", "USA", "Other")
  )
```

``` r
nobel_living_science <- nobel_living %>%
  filter(category %in% c("Physics", "Medicine", "Chemistry", "Economics"))
```

### Exercise 3

``` r
ggplot(data = nobel_living_science, aes(x = country_us)) +
  geom_bar() +
labs(x = "Location of Scholars When Awarded",
       y = "Number of Nobel Prizes",
     ) +
facet_wrap(~ category, nrow = 4)
```

![](lab-03_files/figure-gfm/bar-plot-1.png)<!-- -->

The plots seem to support the claim in the Buzzfeed article. In each
category, there is a higher number of Nobel prizes awarded to scholars
in the US than in other countries. The difference is especially stark
for prizes in economics.

### Exercise 4

``` r
nobel_living_science_born_us <- nobel_living_science %>%
  mutate(
    born_country_us = if_else(born_country == "USA", "USA", "Other")
  )

nobel_living_science_born_us %>%
  count(born_country_us, sort = TRUE)
```

    ## # A tibble: 2 × 2
    ##   born_country_us     n
    ##   <chr>           <int>
    ## 1 Other             123
    ## 2 USA               105

105 winners were born in the US.

### Exercise 5

…

### Exercise 6

…
