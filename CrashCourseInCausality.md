## Notes from A Crash Course in Causality Coursera Course by Dr. A Roy

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
    * 
    

#### II. PreModeling
* Gather data
* Assess data 
* Clean data
* Store data (make backup)
* Analyze & Visualize & EDA
* Create reports


#### III. Risk difference
* Pre-Matching
   * Use CreatetableOne for treatment as outcome to calculate SMD 
   * examine SMD (cutoff < 0.1) 
* Matching 
   * Match package 
   * extract matched pairs (append DF (treated + control) 
   * Use CreateTableOne with the matched data from previous step and examine SDMs
* Outcome Analysis 
   * extract `y_trt = matched$outcome[matched$treatment == 1]` 
   * extract `y_con = matched$outcome[matched$treatment == 1]` 

