# Structure
1. Abstract
2. Benchmarking dialect-to-standard normalization systems
3. Analyzing speaker representations in multi-dialectal NMT
4. Collecting Finnish dialect tweets

# Abstract
1. target of the project
   - improve automatic normalization of dialects text using machine learning translation methods.
   - dialectal patterns extracted from the normalization process.
   - normalization in noiser user-generated contents and the dialectal patterns extracted from it.

# Benchmarking dialect-to-standard normalization systems
1. Models have been used in normalization tasks:
   - SMT
   - NMT: RNN, transformers architecture with attention mechanism, BERT(bi-directional encoders) or GPT(decoder-only architecture with auto regressive mechanism)
   - character-level and BPE(byte-pair encodings) segmentation
   - pre-trained multilingual ByT5 model using byte-level segmentation
  
# Analyzing speaker representations in multi-dialectal NMT
   - through training process, the model would learn embeddings representation for each language label.
