# Structure
1. Abstract
2. Introduction
3. Alignment Methods
4. Data
5. Experimental Setup
6. Results
7. Discussion

# Abstract
1. Topic: Dialect-to-Standard Normalization
2. What have they done? 
   - evaluate various character alignment methods
   - on sentence-level standardization of dialect transcriptions
3. How to evaluate?
4. What have they found?
   - trained alignment methods only show marginal benefits to simple Levenshtein distance.
   - on particular task, eflomal out- performs related methods such as GIZA++ or fast_align by a large margin.

# Introduction
1. the task of aligning characters when both representations are given. (usually only give one source representation)
2. Character Alignment
3. look at the alignments produced by these distance metrics here
4. character transduction and distance computation at sentence level.

# Alignment Methods
1. Dialectometry
    - obtain abstract representations of dialect lanscapes
    - one way: compute distances between phonetic transcriptions of a given word in different dialects. then aggregate the distances over all words of the dataset.
    - Levenshtein distance; vowel-sensitive Lev- enshtein distance; possibility to learn the edit weights from a corpus.
2. Cognate Identification
3. Grapheme-to-phoneme conversion
4. Statistical machine translation

# Data

# Experimental Setup
1. data preparation
   - dialect transcriptions as source
   - orthographic normalization as target
2. alignment methods
3. Symmetrization
4. Adding Adjacent Identicals
5. Evaluation Criteria
   - U-src proportion of unaligned source characters, below 15%
   - U-tgt proportion of unaligned target characters, below 15%
   - V-C proportion of vowel-to-consonant and consonant-to-vowel alignments (disre- garding semi-vowels, nasals, laterals and suprasegmentals), below 1%
   - X proportion of crossing alignment pairs (swaps), below 0.2%