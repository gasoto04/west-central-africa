Institutions and Corruption Analysis
================
Gabriel
2025-03-27

## Setting up and data imports

    ## Warning: package 'DT' was built under R version 4.4.2

    ## Warning: package 'WDI' was built under R version 4.4.3

## 1. Regional Averages of WJP Rule of Law Index 2024.

    ## [1] "Eastern Europe & Central Asia" "Latin America & Caribbean"    
    ## [3] "East Asia & Pacific"           "EU + EFTA + North America"    
    ## [5] "South Asia"                    "Sub-Saharan Africa"           
    ## [7] "Middle East & North Africa"

![](main_files/figure-gfm/regional_averages-1.png)<!-- -->

## 2. Income groups averages comparison for Constraints on Government Powers 2023 and 2024 respectively.

    ## # A tibble: 217 × 5
    ##    Country             Code  Region            `Income group` `Lending category`
    ##    <chr>               <chr> <chr>             <chr>          <chr>             
    ##  1 Afghanistan         AFG   South Asia        Low income     IDA               
    ##  2 Albania             ALB   Europe & Central… Upper middle … IBRD              
    ##  3 Algeria             DZA   Middle East & No… Upper middle … IBRD              
    ##  4 American Samoa      ASM   East Asia & Paci… High income    <NA>              
    ##  5 Andorra             AND   Europe & Central… High income    <NA>              
    ##  6 Angola              AGO   Sub-Saharan Afri… Lower middle … IBRD              
    ##  7 Antigua and Barbuda ATG   Latin America & … High income    IBRD              
    ##  8 Argentina           ARG   Latin America & … Upper middle … IBRD              
    ##  9 Armenia             ARM   Europe & Central… Upper middle … IBRD              
    ## 10 Aruba               ABW   Latin America & … High income    <NA>              
    ## # ℹ 207 more rows

![](main_files/figure-gfm/income_averages-1.png)<!-- -->

## 3. Change over time in the WJP Rule of Law Index for Ghana, Sierra Leone, Liberia compared with the overall average for countries in sub-Saharan Africa from 2014 to 2024.

![](main_files/figure-gfm/time_graph-1.png)<!-- -->

## 4. Statistical Relationship.

### Analysis

From the onset, we can see a strong relationship between the WJP Rule of
Law Index on the Corruption Perception index CPI. Wth everthing else
holding constant, an increase of 1 on the Rule of Law Index, would
result in a 1.17 increase points in CPI. It is worth mentioning that,
through interactions we can see how the Rule of Law Index differs per
region. From the model we can conclude that some regions will see a
greater impact on their CPI, compared to SubSaharan Africa (MiddleEast
and North Africa). Meanwhile other countries see a decrease on their
CPI. This could be related to bias related to, how much of an impact
would better rule of law would impact in Africa, contraray to Europe,
where institutions are more established.

    ## 
    ## Call:
    ## lm(formula = cpi_score ~ wjp_rule_of_law_score * region + log(gdp_usd) + 
    ##     log(population), data = data_final)
    ## 
    ## Residuals:
    ##      Min       1Q   Median       3Q      Max 
    ## -17.9270  -3.2791  -0.1169   3.2566  13.0200 
    ## 
    ## Coefficients:
    ##                                                         Estimate Std. Error
    ## (Intercept)                                            -22.39252    3.20454
    ## wjp_rule_of_law_score                                    1.00218    0.04394
    ## regionEast Asia & Pacific                              -10.83769    2.54320
    ## regionEurope & Central Asia                            -17.40473    2.42116
    ## regionLatin America & Caribbean                        -16.56273    2.74641
    ## regionMiddle East & North Africa                       -28.96746    5.65477
    ## regionNorth America                                    120.41545  133.11116
    ## regionSouth Asia                                         8.03801    4.45385
    ## log(gdp_usd)                                             2.09020    0.28750
    ## log(population)                                         -2.39434    0.31450
    ## wjp_rule_of_law_score:regionEast Asia & Pacific          0.18627    0.04995
    ## wjp_rule_of_law_score:regionEurope & Central Asia        0.21073    0.04645
    ## wjp_rule_of_law_score:regionLatin America & Caribbean    0.25660    0.05462
    ## wjp_rule_of_law_score:regionMiddle East & North Africa   0.50030    0.10566
    ## wjp_rule_of_law_score:regionNorth America               -1.46295    1.66136
    ## wjp_rule_of_law_score:regionSouth Asia                  -0.21983    0.09811
    ##                                                        t value Pr(>|t|)    
    ## (Intercept)                                             -6.988 5.28e-12 ***
    ## wjp_rule_of_law_score                                   22.806  < 2e-16 ***
    ## regionEast Asia & Pacific                               -4.261 2.24e-05 ***
    ## regionEurope & Central Asia                             -7.189 1.33e-12 ***
    ## regionLatin America & Caribbean                         -6.031 2.34e-09 ***
    ## regionMiddle East & North Africa                        -5.123 3.65e-07 ***
    ## regionNorth America                                      0.905 0.365896    
    ## regionSouth Asia                                         1.805 0.071436 .  
    ## log(gdp_usd)                                             7.270 7.54e-13 ***
    ## log(population)                                         -7.613 6.49e-14 ***
    ## wjp_rule_of_law_score:regionEast Asia & Pacific          3.729 0.000203 ***
    ## wjp_rule_of_law_score:regionEurope & Central Asia        4.537 6.45e-06 ***
    ## wjp_rule_of_law_score:regionLatin America & Caribbean    4.698 3.02e-06 ***
    ## wjp_rule_of_law_score:regionMiddle East & North Africa   4.735 2.53e-06 ***
    ## wjp_rule_of_law_score:regionNorth America               -0.881 0.378774    
    ## wjp_rule_of_law_score:regionSouth Asia                  -2.241 0.025284 *  
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 4.637 on 942 degrees of freedom
    ##   (286 observations deleted due to missingness)
    ## Multiple R-squared:  0.9393, Adjusted R-squared:  0.9383 
    ## F-statistic: 971.5 on 15 and 942 DF,  p-value: < 2.2e-16
