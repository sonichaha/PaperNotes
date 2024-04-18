# Strucutre
1. Abstract
2. Introduction
3. Related work
4. Methods
5. Results
6. Discussion

# Abstract
1. Topic: Neural-based machine translation system to translation between varieties of one language
2. What have they done?
    - develop a neural-based variety translation system
    - compare it with a phrase-based SMT system
    - carry out a human evaluation experiment
3. What is their result?
    - performance improvement for both BLEU result and human evaluation result.

# Introduction
1. Their study: test NMT on national varieties of the same language.

# Related Work
1. a rule-based system to adapt texts from BP to EP
2. SMT system trained on a parallel collection from Intel translation memories

# Methods
## what method did they use?
   - recurrent neural networks with an added attention-based mechanism.
## what dataset have they used?
   - aligned Brazilian - European Portuguese parallel corpus of film subtitle dialogues from Open Subtitles available at Opus3
## Systems
### Statistical-based
1. statistical co-occurrences from a parallel corpus at the level of sentences
2. Moses open source toolkit
3. grow-diagonal-final-and word alignment symmetrization, lexicalized reordering, relative frequencies (conditional and posterior probabilities) with phrase discounting, lexical weights, phrase bonus, accepting phrases up to length 10, 5-gram language model with Kneser-Ney smoothing, word bonus
4. MERT (Minimum Error Rate Training) optimisation.
5. adapt from previous work
### Neural-based
1. neural MT computes the conditional probability of the target sentence given the source sentence by means of an encoder-decoder or sequence-to-sequence (seq2seq) archi- tecture, where the encoder reads the source sentence, does a word embedding, and encodes it into an intermediate representation using a bidirectional recurrent neural network with Long Short Term Memory units (LSTM) as activation functions.
2. We use a bidirectional LSTM of 512 units for encoding, a batch size of 32, no dropout and ADAM optimization.
3. architecture was adapted from previous work
4. train on variety aligned dataset

# Conclusion
Our results indicate that the NMT system produces better translations than the SMT system not only in terms of BLEU scores but also according to the judgments of seven native speakers. 