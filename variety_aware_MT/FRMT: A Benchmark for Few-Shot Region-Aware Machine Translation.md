# Structure
1. Abstract
2. Introduction
3. Related Work
4. FRMT Dataset
5. Evaluation Metrics
6. Baseline Models
7. Baseline Model Performance
8. Conclusion

# Abstract
1. Motivation and Achievement
    - present FRMT, a new dataset and evaluation benchmark for Few-shot Region- aware Machine Translation
    - explore automatic evaluation metrics for FRMT
    - validate metrics' correlation with expert human evaluation across both region- matched and mismatched rating scenarios.
    - offer guidelines for how researchers can train, evaluate, and compare their own models.

# Introduction
1. why do research in this topic?
    - most approaches to variety-targeted translation thus far rely on large, labeled training corpora, in many cases these resources are unavailable or expensive to create.
        - what did they do to address this problem?
        - explore a setting for MT where unlabeled training data is plentiful for the desired language pair, but only a few parallel examples (0–100, called “exemplars”) are annotated for the target varieties.
    - One barrier to further research on this issue is the lack of a high-quality evaluation benchmark.
        - what did they do to address this problem?
        - construct and release a dataset with few-shot region-aware translation
        - evaluate existing MT models
        - conduct human expert evaluation
        - validate the correlation of automatic evaluation based on human evaluation on FRMT
        - propose a new targeted metric for lexical accuracy

# Related Work:
- Problems of previous work:
  - Dataset: no good enough dataset for variety/region aware machine translation
  - Evaluation: no correlation between human evaluation and automatic evaluation. no metric to evaluate region-appropriateness.

# FRMT Dataset
- Data Collection:
  - source side: English sentences from Wikipedia
  - target side: professional human translations in the target regional varieties
  - manual verification, MQM protocol
# Evaluation Metrics

# Conclusion
1. what have they done: a new benchmark for evaluating few-shot region-aware ma- chine translation.
2. what have they found: 
    - large-scale generalist model PaLM 540B is impressive, but none of models could compare human performance
3. Problem and Challenge:
    - whether robust few-shot regional control can be achieved at more modest model scales.