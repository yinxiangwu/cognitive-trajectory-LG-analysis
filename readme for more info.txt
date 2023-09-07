#####
Syntax for step 1a: the LatentGold syntax to fit GMMs where I assume linear trajectories with random intercepts and slopes, 
and allow for covariances and residual variances to differ across classes. The syntax specifically fit 3-class GMM. To change the number of class,
change the line of code "Class nominal 3" to another number


#####
Syntax for step1b: the LatentGold syntax to fit GMMs with covariates that are allowed to have both effects on latent class variables and class indicators.
This is achieved by having two lines of equations:
Class <- 1 + age_cat_years + gender + education_;
casi_irt <- 1 | Class + CFactor1 | Class + CFactor2 | Class + casi_visit_dates_years | Class + casi_visit_dates_years CFactor2 | Class + age_cat_years + gender + education_;

It turns out only age has significant effect on both latent class variable and class indicator. Thus to fit the final GMM, change the two line codes to:
Class <- 1 + age_cat_years;
casi_irt <- 1 | Class + CFactor1 | Class + CFactor2 | Class + casi_visit_dates_years | Class + casi_visit_dates_years CFactor2 | Class + age_cat_years;


#####
Syntax for step 3 outcome regression: the LatentGold syntax to perform step-3 analysis to estimate associations of latent class variable with physical activity outcomes
using BCH method.
In the file, I used AP_sit_time_avg as the outcome, which can be changed to another outcome variable.
 


#####
Syntax for step 3 covariate effect: the LatentGold syntax to perform step-3 analysis to estimate the effect of a covariate on latent class variable using ML method
In the file, I used gender as the covariate, which can be changed to another covariate variable.
We can also assess the effects of all covariates in a single model by changing the last line of code to:
Class <- 1 + age_cat_years + gender + education_ + bmi + CESD_Score + DEMO11_ + DEMO20A_ + MED1;
But I don't think this is necessary for Table 1 in the manuscript.