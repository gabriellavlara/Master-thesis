## Motivation
Extract semantically meaningful sentence embeddings: good for large scale semantic similarity, clustering and information retrieval via semantic search'

## BERT vs S-Bert
**Bert ( cross-encoder ):** 
- two sentences passed to transformer, target value predicted
- input: two sentences separated by _SEP_ token
- 12 or 24 levels of multi-head attention, and regression function in the final layer to derive a score 
- no individual sentence embeddings - to solve that, people passed only one sentence to the model, and either averaged over the output or taking only the _CLS_ token
- 
S-BERT ( siamese network ): 
- derives **fixed-size vectors** for input sentences --> add pooling operator to derive this vector by computing (by default) a mean of all output vectors
- trained on SNLI: collection of 570,000 sentence pairs annotated with the labels contradiction, eintailment, and neutral.
- performs well (is it state of the art?) for tasks like sentiment evaluation (SentEval dataset)
- is computationally efficient: **an advantage of transformer networks is the computational efficiency on GPUs** (On a GPU, it is about 9% faster than InferSent and about 55% faster than Universal Sentence Encoder.)
![[sbert-architecture.png]]


## Main takeaways for my work
- **an advantage of transformer networks is the computational efficiency on GPUs**.
### Further reference
- possible reference using reddit sentences (check how they preprocessed / which dataset they used): Learning Semantic Textual Similarity from Conversations.
- what are GloVe embeddings?
- maybe try with S-RoBERTa
- 