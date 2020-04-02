
# GOV 391L STATS II Midterm

- 1) All of the questions can be answerd in no more than 2-3 sencenses.
- 2) There isn't always one single correct answer to a question. 



---


## 2. Explain what it means that OLS is efficient? When is it not?

<br>

$$
\begin{aligned}
\hat \beta_{OLS} &= (X\prime X)^{-1}X\prime Y \\
&= (X\prime X)^{-1}X\prime (X\beta + \epsilon)\\
&= (X\prime X)^{-1}X\prime X\beta + (X\prime X)^{-1}X\prime \epsilon \\
&= \beta + (X\prime X)^{-1} X\prime \epsilon\\ 
\end{aligned}
$$

<br>

$$
\begin{aligned}
Var(\hat \beta_{OLS}) &= Var(\beta + (X\prime X)^{-1} X\prime \epsilon)\\
&= Var((X\prime X)^{-1} X\prime \epsilon) \\
&= (X\prime X)^{-1} X\prime Var(\epsilon) ((X\prime X)^{-1} X\prime)\prime \\
&=(X\prime X)^{-1} X\prime Var(\sigma^2 I) X(X\prime X)^{-1}\\
&= \sigma^2 (X\prime X)^{-1} (X\prime X) (X\prime X)^{-1}\\
&= \sigma^2 (X\prime X)^{-1}\\
\end{aligned}
$$

Therefore, OLS is efficient when $Var(\hat \beta_{OLS}) \leq Var(\beta^{*})$. For this to exist,
- the relationship between Y and X is liner so that $Y = X\beta + \epsilon$
- errors variation is constant so that $Var(\epsilon) = Var(\sigma^2 I)$

  
  

## 3. Explain what it means that OLS is unbiased? When is it not?

With $\hat \beta_{OLS} = \beta + (X\prime X)^{-1} X\prime \epsilon $, OLS is unbiased when
$$
\begin{aligned}
E(\hat \beta_{OLS}) &= E (\beta + (X\prime X)^{-1} X\prime \epsilon) \\
&= E(\beta) + (X\prime X)^{-1} E(X\prime \epsilon)\\
&= \beta
\end{aligned}
$$

For this to exists,
- the relationship between Y and X is liner so that $Y = X\beta + \epsilon$
- errors are on average cancelled out and are not correlatew with X, so that $E(\epsilon) = E(\epsilon |X) = 0$
- there is no perfect collinearity among X variables so that $(X\prime X)^{−1}$ exists

## 4. In your view, what is the most imporant Gauss-Markov assumption? Why?

I think the most important assumption is linearity, because if the relationship between $Y$ and $X$ is not linear, all OLS operations will be not proceduable. Therefore it is always a good practice to plot the relationship of $Y$ against all the IVs we are interested in to verity whether their relationship is approximately linear.

## 5.

You hypothesize that politicians use spending on social services as a political tool and therefore spending will increase when there are more parties in the government trying to "buy" votes and when more sub-populations voce. You obtain data for 22 developed democracies and estimate an OLS regression of social service spending in each country ont he number of parties in government and voter paticipation where:

- `sspendg` is the % of the budget spent on social services (min:13.0, max: 15.0)
- `npgovpw` is the number of parties in the legislature (min: 1, max: 4)
- `vpart` is the % of population that voted in the last election (min: 48.20, max: 91.30)

You also controled for:

- `age`the % of population over 65 (min: 10.10, max: 17.20)
- `ue` the national unemployment rate (min: 0.20, max: 8.30)

Regression results  

```

Call:
lm(formula = sspendg ~ age + ue + npgovpw + vpart, data = data1)

Residuals:
Min 1Q Median 3Q Max
-4.9893 -2.3022 -0.1641 1.8591 7.7695

Coefficients:
Estimated Std.Error t value Pr(>|t|)
(Intercept) -18.03189 8.08013 -2.232 0.03939 *

age 0.71322 0.42485 1.679 0.11148
ue 0.78291 0.37838 2.069 0.05409 .
npgovpw 3.20613 0.82411 3.890 0.00118 **
vpart 0.16626 0.07228 2.300 0.03438 *

---
Signif. codes: 0 ?***? 0.001 ?**? 0.01 ?*? 0.05 ?.? 0.1 ? ? 1

Residual standard error: 3.518 on 17 degrees of freedom
Multiple R-squared: 0.5807,Adjusted R-squared: 0.482
F-statistic: 5.886 on 4 and 17 DF, p-value: 0.003672

````


### (a) Provide a brief interpretation of the results in the relation to your hypothesis.

We estimated the follwoing model $$sspendg = \beta_{0} + \beta_{1}age + \beta_{2}ue + \beta_{3}npgovpw + \beta_{4}vprt$$

Results suggest that

- 1 percentage point increase in voter turnout is **on average** associated with 0.166 percentage point increase in the share of government spending on social services, **all else equal**;

- 1 more party in the legislature is on average associated with 3.206 percentage point increase in the share of government spending on social services, all else equal;

- 1 percentage point increase in th national unemployment rate is on average associated with 0.783 percentage point increase in the share of government spending on social services, all else equal;

- 1 percentage point increase in the share of population over 65 is on average associated with 0.713 percentage point increase in the share of government spending on social services, all else equal.

  

### (b) What does `Intercept` tell you about the model? Is this useful information?

`Intercept` suggests that share of the budget spent on social services will be -18.-32% holding other IVs and controls to zero.

It does not make too much sense in reality because share of the budget spent on social services can never be negative nor zero; it has to be a positive number under 100.

### (c) What is the difference between the F-statistics and Multiple R-squared? Which do you prefer as a measure of model fit and why?

**F-statistics** is a measure of overall significance of the model; it is calculated by testing the hypothesis

$$H_{0}: Y = \beta_{0} + \epsilon $$

$$H_{A}: Y = \beta_{0} + \beta_{1}age + \beta_{2}ue + \beta_{3}npgovpw + \beta_{4}vprt $$

In other words, we test

$$H_{0}: \beta_{1} = \beta_{2} = \beta_{3} = \beta_{4} = 0$$

$$H_{A}: \beta_{1} = \beta_{2} = \beta_{3} = \beta_{4} \neq 0 $$

F-statistics is a better indicator for model fit because it tells us whether all variables included in the model are _jointly_ significant. As a test statistics, it comes up with a threashold that we can compare between models.

**Multiple R-squared** is a measure of how much variation in $Y$ is explained by $X$ variables. Multiple R-squared can be troublesom as it always increases when we add more predictors in the model. Our goal is not to construct a model that maximizes multiple R-squared while overfitting the data; instead we are aiming for a parsimonious model that has the most appropriate fit with the data.

### (d) Reviewer \#1 wants you to include th rsults of a VIF test in the response memo. What is her concern and what will the test tell you?

**VIF** stands for Variance Inflation Factor, it is calculated as

$$VIF = \frac{1}{1 - R^2}$$

  

VIF measures how much variance of $\beta$ is caused by collinearity among $X$ variables

  
### (e) Reviewer \#2 only works with big data and he tells you that your model is clearly wrong because there's no way spending on social services isn't associated with a country's unemployment rate. How do you respond?

In my model, the fact that the coefficient on `ue` is not statistically significant is likely because my sample size is relatively small ($N = 22$). Should I have a larger sample size, the significance of `ue` would increase.

  

### (f) Reviewer \#2 is upset you did not include a variable for the percentage of the population living in ueban areas in each country. You have the data so you reestimate your model and find no relationship between urban population and spending on social services. What is his concern and what do your results suggest regarding this concern?

Reviewer #2 worries that omitting an important variable will bias the model.

Let $Z$ be a variable that has $\lambda$ effect on $Y$. When $Z$ is omitted,

$$
\begin{aligned}
\hat \beta_{OLS} &= (X\prime X)^{-1} X\prime Y\\
&= (X\prime X)^{-1}X\prime (X\beta + Z\lambda + \epsilon) \\
&= (X\prime X)^{-1} X\prime X \beta + (X\prime X)^{-1}X\prime Z\lambda + (X\prime X)^{-1}X\prime \epsilon \\
&= \beta + (X\prime X)^{-1}X\prime Z\lambda + (X\prime X)^{-1}X\prime \epsilon\\
\end{aligned}
$$
  

Therefore,
$$
\begin{aligned}
E(\hat \beta_{OLS}) &= E(\beta + (X\prime X)^{-1}X\prime Z\lambda + (X\prime X)^{-1}X\prime \epsilon)\\
&= E(\beta) + E((X\prime X)^{-1}X\prime Z\lambda) + E((X\prime X)^{-1}X\prime \epsilon))\\
&= \beta + (X\prime X)^{-1}X\prime Z\lambda + (X\prime X)^{-1} E(X\prime \epsilon) \\
&= \beta + (X\prime X)^{-1}X\prime Z\lambda
\end{aligned}
$$

The bias depends on
- $X\prime Z$ or the direction and magnitude of correlation between urban population and other $X$ variables
- $Z\lambda$ or the direction and magnitude of correlation between urban population and spending on social services

The fact that my model shows no relationship between urban population and spending on social services suggests that
- either $X\prime Z = 0$, meaning urban population is not correlated with other X variables;
- or $Z\lambda = 0$, meaning urban population is not correlated with spending on social services

### (g) You originally had data for another 12 countries but your research assistant didn't think there were any democracies in Eastern Europe and deleted all those observations. Why is this a problem? If social service spending is lower than average and the number of parties in the legislature is higher than average in the deleted countries, what will this do to your results?


Droping 12 observations introduces measurement erros in both my dependent varaible and independent variables. Habing measurement erros in the dependent varaible will increase the uncertainty of my model; with measurement erros in independent varaible, my model is no longer BLUE.

If social service spending is lower than average in the deleted countries, $Y$ is overmeasured and it should be corrected as $Y-v$. 

If the number of parties in the legislature is higher than average in the deleted countries, then $X_{1}$ is undermeasured and it should be corrected as $X_{1}+u$.

My original model is $$Y = \beta_{0} + \beta_{1}X + \epsilon$$

But we fit
$$
\begin{aligned}
Y-v &= \beta_{0} + \beta_{1}(X_{1}+u) + \beta_{2}X_{2} \epsilon \\
Y &= \beta_{0} + \beta_{1}X_{1} + \beta_{2}X_{2} + \beta_{1}u + v + \epsilon\\
\end{aligned}
$$

Error $v$ in the dependent variable will increase the variance of the model to $(\sigma^2_{\epsilon} + \sigma^2_{v})(X\prime X)^{-1}$, and our model become less presice.

Error $u$ in the independen variable will bias our coefficient estimates, and the degree and direction dependent on

- $\beta_{0}$, or the correlation between `npgovpw` and other independent variables
- the variace of $u$, or $\frac{\sigma^2_{X}}{\sigma^2_{X} + \sigma^2_{u}}$
