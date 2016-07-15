[![Travis-CI Build Status](https://travis-ci.org/bramtayl/easyformatr.svg?branch=master)](https://travis-ci.org/bramtayl/easyformatr) [![codecov.io](https://codecov.io/github/bramtayl/easyformatr/coverage.svg?branch=master)](https://codecov.io/github/bramtayl/easyformatr?branch=master)

Friendly Time Formats
=====================

Have you ever had to build a way too complicated time format?

``` r
my_time_format = "%Ey/%b/%0d%t%0I:%0M:%0S3 %p %Z"
```

How about a too complicated string format?

``` r
my_string_format = "%1$+03.0f and 1%% and %1$-+3.0f"
```

No human could read this. easyformatr allows you to build understandable R format strings.

``` r
library(easyformatr)
library(magrittr)
```

``` r
easy_format(list(double %>% 
                     zero_pad,
                   "1%",
                   double %>% 
                     left_justify) %>%
                use_input(1) %>%
                always_sign %>%
                before_decimal(3) %>%
                after_decimal(0),
              sep = " and ")
```

    ## %1$+03.0f and 1%% and %1$-+3.0f

``` r
easy_format(list(year %>% religious, 
                 "/", 
                 month %>% name) %>%
              short,
            "/", 
            list(day,
                 tab,
                 hour %>% twelve,
                 ":",
                 minute) %>%
              roman,
            ":",
            second %>% digits(3),
            
            " ",
            am_pm,
            " ",
            timezone)
```

    ## %Ey/%b/%0d%t%0I:%0M:%0S3 %p %Z

Inspired by kevinushey/rex

Installation
============

``` r
# for cran version
install.packages("easyformatr")

# for bleeding edge:
devtools::install_github("easyformatr")
```
