# Structure
1. Abstract
2. Introduction
3. Measuring phone(me)s, syllables, and words
   - Technical considerations
   - Linguistic and developmental considerations
4. Methods
   - Broad class diarization
   - Speech feature extraction
     - Phone recognition
     - Syllable count estimation
   - Mapping of features into ALUCs
5. Experiments
   - data
   - metrics
   - setup
6. Results
   - result and discussion for each experiment
7. Conclusions and limitations

# Abstract
- what problem are they trying to address?
  - quantify young children's language environments
  - traditional way: LENA, estimates the number of adult words
  - their limitation: not language independent. the relationship between observable acoustic patterns and language-specific lexical entities is far from uniform across human languages.
- what's their improvement?
  - measure other linguistic units, for example, phonemes, or syllables instead of words.
  - check rationality, advantages and disadvantages
  - develop a system ALICE
- what's their result?
  - phoneme counts is somewhat more accurate than syllables or words; all three are highly correlated with human annotations.
- what's their contribution?
  - open-source implementation of ALICE
  - enable automatic phoneme, syllable, and word count estimation from child-centered audio recordings.

(how computational language modeling, including speech reconizer, to quantify the quality and quantity of language input for children chould be used in language acquisition, conitive science studies?)


