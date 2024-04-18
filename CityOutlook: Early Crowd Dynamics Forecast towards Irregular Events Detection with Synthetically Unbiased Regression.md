# Structure
1. Abstract
2. Introduction
3. Problem Setting and Baseline
4. Problem Method
5. Experiment
6. Conclusion
# Abstract
1. Topic: crowd dynamic prediction
2. Problem: scarcity of anomalous events, a large model bias, could not quantify the number of visitors in anomalous crowd gathering 
3. Potential Solution: Importance Weighting, problem: hard to divide data into abnormal and normal sets, solution: anomaly-aware data annotation scheme.
4. Solution in the paper: CityOutlook model, unbiased regression with importance-biased reweighting.
5. Evaluation data set: mobility and transit search logs
6. Conclusion: same accuracy in normal dynamic forecasting, better performance on crow anomaly forecast.
# Introduction
1. Why this topic: to detect regular or irregular events, enable countermeasures for anomalous human movements.
2. Related Research Phrase: 
   1. simulating the crowd flows using regressive models (problem: short-term forecasting)
   2. problem: rarity of anomalous events, data imbalance, bias in regression model
3. Potential Solution, Hypothesis: 
   1. Importance weighting (IW) involves reweighting the loss function to be minimized (e.g., ordinary least squared loss) and provides an unbiased estimate for the distribution of anomalous data.
   2. Problem in employing: data division
4. Solution: 
   1. a reggression model, with importance-reweighting of anomalous data. 
   2. the model regresses the irregularity score of crowd dynamics from people’s schedule patterns and contextual information such as time, weather, and weekday or weekend (how to get the irregularity score and contextual information?)
   3. leverage the concept of IW to penalize the loss to reduce the estimation bias for anomalous crowd dynamics.(how to penallize the loss for anomalous dynamics?)
   4. an anomaly-aware data annotation scheme, generate the quantified relevance of anoamlity without depending on the contextual information(how?)

# Problem Setting
1. Definition:
   1. time segment: t
   2. point of interest (city region): l
   3. crowd density(the number of mobility records in a certain
area l in a certain time segment t): $y^{(l)}_{d,t}$
   4. future crowd = transit search queries: $s^{(l)}_{d,t|d'}$, with schedule day and time d,t, destination l, search date d'
   5. the scheduled crowd density set would be $S^{(l)}_{d,t} = \{s^{(l)}_{d,t|d-i} | i = p_d, p_d+1, ..., p_d+p_w\}$, pd is the earliest that should be considered and pw is the range of days considered (why just do the summation)
   6. irregularity score $v^{(l)}_{d,t} = (y^{(l)}_{d,t} - \bar{y}^{(l)}_{d,t}), \bar{y}^{(l)}_{d,t}$ is the normal dynamic forecasted by the schedule crowd density and contextual information (is $\bar{y}^{(l)}_{d,t}$ a constant).
2. Baseline: Supervised-CityProphet
   - This model could predict the irregularity score $v^{(l)}_{d,t}$ by associated the mobility logs and scheduled patterns $S^{(l)}_{d,t}$.
   1. regression model $v^{(l)}_{d,t} = f(\xi^{(l)}_{d,t}|\theta), \theta$ is the weights
   2. input variables of the model, $\xi^{(l)}_{d,t} = \{\xi^{(l)}_{d,t-j|d-i}|\xi^{(l)}_{d,t-j|d-i}=(s^{(l)}_{d,t-j|d-i} - \bar{s}^{(l)}_{d,t})/\bar{s}^{(l)}_{d,t}\}, j = -1, 0, 1$, a set of deviations between schedule crowd density by search queries and expectation of crowd density by contextual information.
   3. $\bar{s}^{(l)}_{d,t}$: the normal dynamics, defined by expectation of crowd density by contextual information, bilinear Poisson regression.
   4. $\bar{y}^{(l)}_{d,t}$ and $\bar{s}^{(l)}_{d,t}$ are predicted by bilinear Poisson regression with the contextual information as inputs.
   5. Ordinary Least Squared(OLS) Loss to inferr the optimal weights.
   6. Problem: tend to ignore rare patterns
3. Proposed Method: CityOutlook
   1. Bias Reduction by Importance Weighting
      1. relevance of anomalous patterns <- closeness of the normal and abnormal data distributions.
      2. density ratio estimation-based IW technique
      3. importance $w(\xi) = \frac{P(s=1|\xi)}{P(s=0|\xi)}$, s=1 means the density is abnormal while s=0 means normal.
      4. importance weighted least squared loss can be minimized: $min_{\theta}[\frac{1}{N}\sum_n \frac{P(s=1|\xi)}{P(s=0|\xi)}L(v, f(\xi^{(l)}_{d,t}|\theta))]$, which means we pay more attention to the data $\xi$ which has more probability to be considered as abnomalous
      5. to allow the model to learn normal and abnomalous data at the same time, we use parameter $\beta \in [0,1]$, $\widetilde{w}(\xi) = \frac{P(s=1|\xi)}{\beta P(s=1|\xi)+(1-\beta)P(s=0|\xi)}$
      6. question is, how to get the normal and abnormal data distributions, calculate $P(s|\xi)$? isn't the probability $P(s=1|\xi)$ similar to the irregularity score? (Yes but it's only used to train, we don't need to predict it)
   2. Heterogeneous Anomaly-Aware Annotation Scheme
      1. upper bound for normality $\bar{v}_{thre}$
      2. ![alt text](https://file%2B.vscode-resource.vscode-cdn.net/Users/zhitaoliang/Documents/study/master%20thesis/code/PaperNotes/cityoutlook_1.png?version%3D1708776026787)
      3. by baye's theorem, $\widetilde{w}(\xi) = \frac{P(s=1, \xi)}{\beta P(s=1, \xi)+(1-\beta)P(s=0, \xi)}$
   3. Parameter Learning and Dynamics Forecast
      1. Learning Process: get parameter from the optimization with L2 regularization term ![alt text](https://file%2B.vscode-resource.vscode-cdn.net/Users/zhitaoliang/Documents/study/master%20thesis/code/PaperNotes/cityoutlook_2.png?version%3D1708776829861)
      2. Forecasting Process:
         1. inferred irregularity score $\widehat{v}$
         2. crowd density $\widehat{y}^{(l)}_{d,t} = (1+\widehat{v})\bar{y}^{(l)}_{d,t}$
   4. Experiments
      1. dataset: mobility logs as crowd dynamics; transit search queries as scheduled crowd dynamics.
      2. Setup and Baseline：
         1. normal crow dynamics predicted by poisson distribution based on contextual information.
         2. hyper parameter, how to decide?
         3. Evaluation
            1. irregularity score forecast and crowd density forecast.
            2. evaluation metrics: NS-MAE, AS-MAE
            3. comparative model: CityProphet
      3. The proposed method achieved a dramatic performance improvement in forecasting anomalous crowd dynamics while maintaining the same level for normal crowd dynamics simultaneously
4. Question:
   1. Why we predict the deviation by the schedule crowd density's deviations, instead of predict the crowd dynamics directly? To combine with the contextual information!