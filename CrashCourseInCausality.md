## Notes from A Crash Course in Causality Coursera Course by Dr. A Roy
===

### Risk Ratio modeling 

#### I. Software 
* R/RStudio
* Libraries
    * Matching 
    * tableone
    * MatchIt
    * ipw
    * sandwich # for robust variance estimation
    * survey 
    * ivpack 
    * rcbalance
    

#### II. PreModeling
1. Gather data
2. Assess data 
3. Clean data
4. Store data (make backup)
5. Analyze & Visualize & EDA
6. Create reports


#### III. Risk difference using distances
* Pre-Matching
   * Use CreatetableOne for treatment as outcome to calculate SMD 
   * Examine SMD (cutoff < 0.1) 
* Matching 
   * Match package to create Matched Pairs
   * Extract matched pairs (append DF (treated + control) to create `matched` dataframe
   * Use CreateTableOne with the matched data from previous step and examine SDMs
* Outcome Analysis 
   * Etract `y_trt = matched$outcome[matched$treatment == 1]` 
   * Extract `y_con = matched$outcome[matched$treatment == 1]` 
   * Carry out `t-test (t.test(y_trt = y_con))`
   * Also can perform McNemar Test using `table(y_trt, y_con)`
      * analyze the concordant and disconcordant pairs

* Use rcbalance for matching
* Use Table one for Tables/Figures
* Causal RR or OR use GEE or logit link function

#### IV Propensity Scores for Matching

Probability of receiving treatment given control, and covariates X. 
[comment]: # ( Taken from: https://stackoverflow.com/a/47798853/1474291 )
<img src="https://latex.codecogs.com/svg.image?\Pi_{i}&space;=&space;P(A=1|X_{i})"
title="\Large \Pi_{i}=P(A=1|X_{i})"/>
 
* `psmodel <- glm(y ~ X, family=binomial(), data=data)`
* Calculate pscore using `pscore <- psmodel$fittedvalues
    * One could use MatchIt package and calculate pscore directly and create matched pairs
* Use PS to calculate logit; then use logit for matching 
* `pm <- Match(tr=data$treatment, M=1, x=logit(pscore), replace=FALSE)`
    * Note logit is a custom function; `log(p) - log(1-p)`
* Create matched pair from `pm`
* Test SMD 
* $`\sqrt{2}`$`



