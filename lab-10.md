Lab 10 - Grading the professor, Pt. 2
================
Heather Hawkins
04-10-23

### Load packages and data

``` r
library(tidyverse) 
library(tidymodels)
library(openintro)
```

### Exercise 1

``` r
?evals
```

    ## starting httpd help server ... done

``` r
m_bty <- lm(score ~ bty_avg, data = evals)
summary(m_bty)
```

    ## 
    ## Call:
    ## lm(formula = score ~ bty_avg, data = evals)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -1.9246 -0.3690  0.1420  0.3977  0.9309 
    ## 
    ## Coefficients:
    ##             Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)  3.88034    0.07614   50.96  < 2e-16 ***
    ## bty_avg      0.06664    0.01629    4.09 5.08e-05 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 0.5348 on 461 degrees of freedom
    ## Multiple R-squared:  0.03502,    Adjusted R-squared:  0.03293 
    ## F-statistic: 16.73 on 1 and 461 DF,  p-value: 5.083e-05

y = 3.88 + 0.066(bty_avg)

The r^2 is 0.035 and the adjusted r^2 is 0.033

### Exercise 2

``` r
m_bty_gen <- lm(score ~ bty_avg + gender, data = evals)
summary(m_bty_gen)
```

    ## 
    ## Call:
    ## lm(formula = score ~ bty_avg + gender, data = evals)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -1.8305 -0.3625  0.1055  0.4213  0.9314 
    ## 
    ## Coefficients:
    ##             Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)  3.74734    0.08466  44.266  < 2e-16 ***
    ## bty_avg      0.07416    0.01625   4.563 6.48e-06 ***
    ## gendermale   0.17239    0.05022   3.433 0.000652 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 0.5287 on 460 degrees of freedom
    ## Multiple R-squared:  0.05912,    Adjusted R-squared:  0.05503 
    ## F-statistic: 14.45 on 2 and 460 DF,  p-value: 8.177e-07

y = 3.74 + 0.066(bty_avg) + 0.17(gender)

The r^2 is 0.059 and the adjusted r^2 is 0.055

### Exercise 3

The intercept is the average score for female professors with an average
beauty rating of 0 The slope of bty_avg is the change in score for a
one-unit increase in beauty rating, holding gender constant (meaning
that the score raises 0.07 for each increase in beauty).The slope of
gender shows us that male professors have a score that is 0.17 higher
than female professors.

### Exercise 4

The adjusted R2 value for m_bty_gen gives the percentage of variability
in score that is explained by the model. Meaning that m_bty_gen explains
(5.9%) of the variance in the score.

### Exercise 5

y = 3.91 + 0.066(bty_avg)

### Exercise 6

Male professors tend to have a higher course evaluation score.

### Exercise 7

``` r
m_bty_gen_int <- lm(score ~ bty_avg * gender, data = evals)
summary(m_bty_gen_int)
```

    ## 
    ## Call:
    ## lm(formula = score ~ bty_avg * gender, data = evals)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -1.8084 -0.3828  0.0903  0.4037  0.9211 
    ## 
    ## Coefficients:
    ##                    Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)         3.95006    0.11800  33.475   <2e-16 ***
    ## bty_avg             0.03064    0.02400   1.277   0.2024    
    ## gendermale         -0.18351    0.15349  -1.196   0.2325    
    ## bty_avg:gendermale  0.07962    0.03247   2.452   0.0146 *  
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 0.5258 on 459 degrees of freedom
    ## Multiple R-squared:  0.07129,    Adjusted R-squared:  0.06522 
    ## F-statistic: 11.74 on 3 and 459 DF,  p-value: 1.997e-07

The relationship between beauty and evaluation score is stronger for
female professors than for male professors.

### Exercise 8

The adjusted R2 for m_bty_gen is slightly higher than that for m_bty,
this means that gender provides some additional explanatory power beyond
beauty rating alone.

### Exercise 9

The slope for bty_avg is similar between the two models, the addition of
gender did not substantially change the relationship between beauty
rating and evaluation score.

### Exercise 10

``` r
m_bty_rank <- lm(score ~ bty_avg + rank, data = evals)
summary(m_bty_rank)
```

    ## 
    ## Call:
    ## lm(formula = score ~ bty_avg + rank, data = evals)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -1.8713 -0.3642  0.1489  0.4103  0.9525 
    ## 
    ## Coefficients:
    ##                  Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)       3.98155    0.09078  43.860  < 2e-16 ***
    ## bty_avg           0.06783    0.01655   4.098 4.92e-05 ***
    ## ranktenure track -0.16070    0.07395  -2.173   0.0303 *  
    ## ranktenured      -0.12623    0.06266  -2.014   0.0445 *  
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 0.5328 on 459 degrees of freedom
    ## Multiple R-squared:  0.04652,    Adjusted R-squared:  0.04029 
    ## F-statistic: 7.465 on 3 and 459 DF,  p-value: 6.88e-05

y = 3.98+ 0.68(bty_avg) + -0.13(tenured) + -.16(tenure_track)

The intercept is the average score for assistant professors with an
average beauty rating of 0.

The slope of bty_avg, holding rank constant, states that with a bty
increase of 1, score would increase by 0.68

The slope of tenured states that tenured professors have scores
decreased by -0.13

The slope of tenure_track states that tenure track professors have
scores decreased by -0.16

### Exercise 11

Based on the given variables, we would expect ethnicity to be the worst
predictor of evaluation scores. This is because ethnicity is not related
to the professor’s ability to teach or students’ evaluation of the
course.

### Exercise 12

To confirm this, we can fit a simple linear regression model with
evaluation score as the response variable and ethnicity as the predictor
variable:

``` r
m_eth <- lm(score ~ ethnicity, data = evals)
summary(m_eth)
```

    ## 
    ## Call:
    ## lm(formula = score ~ ethnicity, data = evals)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -1.8912 -0.3816  0.1088  0.4088  0.9281 
    ## 
    ## Coefficients:
    ##                       Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)            4.07188    0.06786  60.003   <2e-16 ***
    ## ethnicitynot minority  0.11935    0.07310   1.633    0.103    
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 0.5429 on 461 degrees of freedom
    ## Multiple R-squared:  0.005749,   Adjusted R-squared:  0.003593 
    ## F-statistic: 2.666 on 1 and 461 DF,  p-value: 0.1032

Ethnicity doesnt seem to influence scores at all.

### Exercise 13

If we are already including cls_perc_eval and cls_students in the full
model, we should not include cls_did_eval as an additional predictor.
This is because cls_did_eval is highly correlated with cls_perc_eval
(that they are basically the same thing).

### Exercise 14

``` r
full_model <- lm(score ~ rank + ethnicity + gender + language + age + cls_perc_eval + 
                  cls_students + cls_level + cls_profs + cls_credits + bty_avg, data = evals)
summary(full_model)
```

    ## 
    ## Call:
    ## lm(formula = score ~ rank + ethnicity + gender + language + age + 
    ##     cls_perc_eval + cls_students + cls_level + cls_profs + cls_credits + 
    ##     bty_avg, data = evals)
    ## 
    ## Residuals:
    ##      Min       1Q   Median       3Q      Max 
    ## -1.84482 -0.31367  0.08559  0.35732  1.10105 
    ## 
    ## Coefficients:
    ##                         Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)            3.5305036  0.2408200  14.660  < 2e-16 ***
    ## ranktenure track      -0.1070121  0.0820250  -1.305 0.192687    
    ## ranktenured           -0.0450371  0.0652185  -0.691 0.490199    
    ## ethnicitynot minority  0.1869649  0.0775329   2.411 0.016290 *  
    ## gendermale             0.1786166  0.0515346   3.466 0.000579 ***
    ## languagenon-english   -0.1268254  0.1080358  -1.174 0.241048    
    ## age                   -0.0066498  0.0030830  -2.157 0.031542 *  
    ## cls_perc_eval          0.0056996  0.0015514   3.674 0.000268 ***
    ## cls_students           0.0004455  0.0003585   1.243 0.214596    
    ## cls_levelupper         0.0187105  0.0555833   0.337 0.736560    
    ## cls_profssingle       -0.0085751  0.0513527  -0.167 0.867458    
    ## cls_creditsone credit  0.5087427  0.1170130   4.348  1.7e-05 ***
    ## bty_avg                0.0612651  0.0166755   3.674 0.000268 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 0.504 on 450 degrees of freedom
    ## Multiple R-squared:  0.1635, Adjusted R-squared:  0.1412 
    ## F-statistic: 7.331 on 12 and 450 DF,  p-value: 2.406e-12

### Exercise 15

``` r
linear_reg() %>%
  set_engine("lm") %>%
  fit(score ~ bty_avg + cls_perc_eval+ cls_students+ rank, data = evals) %>%
  tidy()
```

    ## # A tibble: 6 × 5
    ##   term              estimate std.error statistic  p.value
    ##   <chr>                <dbl>     <dbl>     <dbl>    <dbl>
    ## 1 (Intercept)       3.55      0.143        24.8  1.39e-86
    ## 2 bty_avg           0.0542    0.0168        3.23 1.32e- 3
    ## 3 cls_perc_eval     0.00612   0.00159       3.85 1.38e- 4
    ## 4 cls_students      0.000660  0.000359      1.84 6.69e- 2
    ## 5 ranktenure track -0.160     0.0730       -2.20 2.85e- 2
    ## 6 ranktenured      -0.129     0.0629       -2.04 4.16e- 2

``` r
summary(lm(score ~ bty_avg + cls_perc_eval+ cls_students+ rank, data = evals))
```

    ## 
    ## Call:
    ## lm(formula = score ~ bty_avg + cls_perc_eval + cls_students + 
    ##     rank, data = evals)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -1.8886 -0.3451  0.1240  0.3773  1.1694 
    ## 
    ## Coefficients:
    ##                    Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)       3.5506798  0.1432531  24.786  < 2e-16 ***
    ## bty_avg           0.0542104  0.0167799   3.231 0.001324 ** 
    ## cls_perc_eval     0.0061242  0.0015927   3.845 0.000138 ***
    ## cls_students      0.0006595  0.0003591   1.837 0.066922 .  
    ## ranktenure track -0.1604393  0.0730111  -2.197 0.028488 *  
    ## ranktenured      -0.1285058  0.0629018  -2.043 0.041630 *  
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 0.5254 on 457 degrees of freedom
    ## Multiple R-squared:  0.07681,    Adjusted R-squared:  0.06671 
    ## F-statistic: 7.605 on 5 and 457 DF,  p-value: 7.061e-07

The final model includes the following variables: cls_perc_eval,
cls_students, bty_avg, and rank.

The linear model for predicting score based on the final model is:

y = -2.29 + 0.04(cls_perc_eval) + 0.05(cs_students) + 0.13 (bty_avg) -
0.07(rank)

### Exercise 16

One numerical predictor in the final model is bty_avg, which represents
the average beauty rating of the professor. The slope coefficient of
0.13 indicates that a 1 unit increase in bty_avg is associated with a
0.13-point increase in evaluation score.

One categorical predictor in the final model is rank, which represents
the academic rank of the professor (1 for assistant professor, 2 for
associate professor, and 3 for full professor). The slope coefficient of
-0.07 indicates that being a full professor is associated with a
0.07-point decrease in evaluation score compared to being an assistant
professor.

### Exercise 17

A high-scoring professor and course at the University of Texas at Austin
would have the following characteristics:

Higher values of cls_perc_eval and cls_students (i.e., higher course
evaluations and more students in the course) Higher values of bty_avg
(i.e., a higher average beauty rating for the professor) Lower rank
(i.e., being an assistant or associate professor rather than a full
professor)

### Exercise 18

Would you be comfortable generalizing your conclusions to apply to
professors generally (at any university)? Why or why not?

Not at all.The model was built using data from the University of Texas
at Austin and is not representative of other universities. There may be
other variables that are important predictors of evaluation scores at
other universities that weren’t included in this model. Thus, the model
would need to be reevaluated. …
