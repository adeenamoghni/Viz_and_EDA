Data Visualization
================
2024-09-26

    ## using cached file: C:\Users\adeen\AppData\Local/R/cache/R/rnoaa/noaa_ghcnd/USW00094728.dly

    ## date created (size, mb): 2024-09-26 10:18:38.832335 (8.668)

    ## file min/max dates: 1869-01-01 / 2024-09-30

    ## using cached file: C:\Users\adeen\AppData\Local/R/cache/R/rnoaa/noaa_ghcnd/USW00022534.dly

    ## date created (size, mb): 2024-09-26 10:19:04.863575 (3.94)

    ## file min/max dates: 1949-10-01 / 2024-09-30

    ## using cached file: C:\Users\adeen\AppData\Local/R/cache/R/rnoaa/noaa_ghcnd/USS0023B17S.dly

    ## date created (size, mb): 2024-09-26 10:19:13.03401 (1.038)

    ## file min/max dates: 1999-09-01 / 2024-09-30

    ## Warning: Removed 17 rows containing missing values or values outside the scale range
    ## (`geom_point()`).

![](Data_Visualization_Day2_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->

Scales- start out with x and y

    ## Warning in transformation$transform(x): NaNs produced

    ## Warning in scale_y_continuous(limits = c(0, 30), transform = "sqrt"): sqrt
    ## transformation introduced infinite values.

    ## Warning: Removed 302 rows containing missing values or values outside the scale range
    ## (`geom_point()`).

![](Data_Visualization_Day2_files/figure-gfm/unnamed-chunk-4-1.png)<!-- -->

    ## Warning in transformation$transform(x): NaNs produced

    ## Warning in scale_y_continuous(limits = c(0, 30), transform = "sqrt"): sqrt
    ## transformation introduced infinite values.

    ## Warning: Removed 302 rows containing missing values or values outside the scale range
    ## (`geom_point()`).

![](Data_Visualization_Day2_files/figure-gfm/unnamed-chunk-5-1.png)<!-- -->

    ## Warning in transformation$transform(x): NaNs produced

    ## Warning in scale_y_continuous(limits = c(0, 30), transform = "sqrt"): sqrt
    ## transformation introduced infinite values.

    ## Warning: Removed 302 rows containing missing values or values outside the scale range
    ## (`geom_point()`).

![](Data_Visualization_Day2_files/figure-gfm/unnamed-chunk-6-1.png)<!-- -->

Bonus content

Usinf diff data sets in diff geoms

    ## Warning: Removed 1 row containing missing values or values outside the scale range
    ## (`geom_point()`).

![](Data_Visualization_Day2_files/figure-gfm/unnamed-chunk-7-1.png)<!-- -->

![](Data_Visualization_Day2_files/figure-gfm/unnamed-chunk-8-1.png)<!-- -->

    ## Warning: Removed 17 rows containing missing values or values outside the scale range
    ## (`geom_point()`).

    ## `geom_smooth()` using method = 'loess' and formula = 'y ~ x'

    ## Warning: Removed 17 rows containing non-finite outside the scale range
    ## (`stat_smooth()`).
    ## Removed 17 rows containing missing values or values outside the scale range
    ## (`geom_point()`).

![](Data_Visualization_Day2_files/figure-gfm/unnamed-chunk-9-1.png)<!-- -->

## Data Manipulation

    ## Warning: There was 1 warning in `mutate()`.
    ## ℹ In argument: `name = fct_relevel(name, c("Molokai_HI", "Central_Park_NY",
    ##   "Waterhole_WA"))`.
    ## Caused by warning:
    ## ! 1 unknown level in `f`: Central_Park_NY

    ## Warning: Removed 17 rows containing non-finite outside the scale range
    ## (`stat_ydensity()`).

![](Data_Visualization_Day2_files/figure-gfm/unnamed-chunk-10-1.png)<!-- -->

``` r
pulse_df =
  read_sas("data/public_pulse_data.sas7bdat") %>% 
  janitor:: clean_names() %>% 
  pivot_longer(
    cols = bdi_score_bl:bdi_score_12m,
    names_to = "visit",
    values_to = "bdi_score",
    names_prefix = "bdi_score_"
  ) %>% 
  mutate(visit= ifelse(visit == "bl", "00m", visit))
pulse_df %>% 
  ggplot(aes(x = visit, y = bdi_score)) +
  geom_boxplot()
```

    ## Warning: Removed 879 rows containing non-finite outside the scale range
    ## (`stat_boxplot()`).

![](Data_Visualization_Day2_files/figure-gfm/unnamed-chunk-11-1.png)<!-- -->
