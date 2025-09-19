1. Embed both **H** (human generated) and **S** (synthetic) fake news in the same semantic space using a sentence embedder. 
2. Perform k-ANN search using *Faiss *. 
   For each s in S, get **top K neighbours** **by cosine similarity**
$$
 N_{K}(s) \in H
$$
3. ??? Re-rank to find semantically close pairs $$
(h_{i}, s_{i})
$$
4. Use another evaluation metric (maybe human evaluation?) to assert if $$
(h_{i}, s_{i})
$$ have the same false claim, or how close they are to each other.
5. Compute **precision and recall** -> but what is ground truth? Should I consider them true if they come from the same "parent"-news in R? Is there even a way to define this?
#### Goal: Evaluate how similar the LLM-generated fakes are to the human-generated ones. 
