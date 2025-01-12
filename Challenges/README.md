Exercises - Follow Me: Introduction to social media analysis in R
================
Maria Prokofieva, Anna Quaglieri, Saskia Freytag
useR! July 2018

-   [1. Twitter challenge](#twitter-challenge)

For the last hour we want you to apply your new knowledge to your favourite social media platform. So pick one of the exercises and have fun!

1. Twitter challenge
--------------------

Compare tweets which mention Harry to tweets mentioning Meghan in the Royal 👑 Wedding time series. You can find the data in the folder `Twitter_Tutorial_data/combined_royal_time_series.csv` (also on github <https://github.com/annaquaglieri16/Royal-Twitter-Workshop-useR-2018/tree/master/Twitter_Tutorial_data>). Produce a plot that showcases your findings and post it to twitter using the hashtags \#useR2018, \#rstats and \#socialmediachallenge. Extra points for being able to upload your results trough R!

The data provided is exactly the same as the `all_words` data frame created during the tutorial (replicated tweets are removed)

``` r
library(tidyverse)
library(here)

# Load data
all_words <- read_csv(file.path(here(),"Twitter_Tutorial_data/combined_royal_time_series.csv"))
```

Here are some hints for the analysis to detect `Harry` and `Meghan` words within the tweets:

``` r
mutate(Harry = str_detect(string = text ,pattern = "harry"),
    Meghan = str_detect(string = text ,pattern = "meghan|megan|markle")) %>%
mutate(Harry_Meghan = case_when(Harry & !Meghan ~ "Harry",
                                  Meghan & !Harry ~ "Meghan",
                                  Harry & Meghan ~ "Harry_Meghan",
                                  TRUE ~ "none"))
```

-   wordcloud
-   sentiment analysis
-   timeseries
-   <https://www.tidytextmining.com/twitter.html>

Here are some hints for uploading through R:

-   `twitteR::updateStatus`
-   <https://blog.rladies.org/post/deployment/>
