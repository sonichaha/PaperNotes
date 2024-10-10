# Structure
- Introduction
- Background
- Methods
- Evaluation
- Results
- Discussion and Conclusions

# Abstract
- what's their objective and what have they done?
  - model age-dependent linguistic properties in CDS
  - generate synthetic CDS in an age-approapriate manner, thereby scaling the original dataset in size
  - compare characteristics of the generated CDS against the real speech addressed at children of different ages
  - systematic characterization of age-dependent linguistic properties
- what's the results?
  - synthetic CDS
  - LM manages to capture age-dependent changes in CDS, except for a slight difference in the effective vocabulary size.
  - how all measured aspects of the CDS change with children’s age

# Introduction
- Their research problems in mind:
  - explore to what extent child language development can be explained in terms of learning from (limited) language input accessible to real infants
  - to what extent speech and language technology tools could be made as data efficient as human learners.
- Problems in existing work:
  - Existing modeling studies are largely based on unrealistically small CDS datasets or larger read speech datasets in adult-directed speech (ADS) style
  - no large enough good-quality CDS speech corpora to represent infant language experience at a realistic scale, nor is there enough transcribed CDS data to support speech synthesis to create age-appropriate CDS
  - how they address this problem?
    - we propose a conceptual solution to the CDS data availability problem through stochastic generation of synthetic yet realistic CDS at a natural scale; first generating transcripts of parents’ verbal interactions with their children, and then synthesizing the transcripts into CDS with a text-to- speech (TTS) system.

# Background
- What problems do they want to address?
  - the existing studies with LMs do not model the developmental trajectory of child language skills as a function of learner’s age
  -  data limitation problem

# Methods
- Overview
  - four stages:
    - LM training by CDS text transcripts conditional to child factors
    - input child factors, use LM to generate synthetic CDS data
    - Comparison of the CDS data with synthetic CDS data
    - convert text CDS data to speech data(not covered)
- LM architecture, training, and text generation
  - an embedding layer for age conditioning
  - BERT embedding
  - GPT decoder only architecture

# Evaluation
- type-to-token ratio (TTR) of lexemes as a measure of lexical richness
- the mean number of words and the mean number of dependencies of the root as a proxy for syntactic complexity
- Mean utterance perplexity was calculated as a holistic measure for syntax, lexicon, and general acceptability of the generated output.