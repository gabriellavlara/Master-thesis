## Motivation
Extract semantically meaningful sentence embeddings: good for large scale semantic similarity, clustering and information retrieval via semantic search'

## BERT vs S-Bert
**Bert ( cross-encoder ):** 
- two sentences passed to transformer, target value predicted
- input: two sentences separated by _SEP_ token
- 12 or 24 levels of multi-head attention, and regression function in the final layer to derive a score 
- no individual sentence embeddings: 
S-BERT ( siamese network ): derives fixed-size vectors for input sentences