1. Embed both **H** (human generated) and **S** (synthetic) fake news in the same semantic space using a sentence embedder (e.g. **S-BERT**, **GTE**. 
2. Perform k-ANN search using *Faiss *. 
   For each s in S, get **top K neighbours** **by cosine similarity**
$$
 N_{K}(s) \in H
$$
3. ??? Re-rank to find semantically close pairs $$
(h_{i}, s_{i})
$$
4. Use another evaluation metric to assert if
$$
(h_{i}, s_{i})
$$ 
have the same false claim, or how close they are to each other, such as *dot-product, angular-similarity (Spotify), BERT-score for how close generated vs. "ideal" text is*
F.e. *sentiment analysis?*

#### Goal: Evaluate how similar the LLM-generated fakes are to the human-generated ones. 
#### Potential Goal: Have a "check-worthy" metric 
The top-k nearest neighbors to a synthetic fake S would be the ones with labeled as "check-worthy", and would then be flagged. This is a proactive approach to fake-news checking. 

