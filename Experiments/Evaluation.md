1. Precision@k: of all the top-k nearest neighbors to a synthetic fake S, how many were actually fake H_fake?
   
2. Recall@k: of all the H_fake, how many did the check-worthy system correctly identify as fake?

3. For each model in M, average results. Find out which one produces synthetic fakes that retrieve more human fakes

4. For each prompting strategy in P, average results. Check which prompting style generates fakes that align most with real ones 

**Likelihood of falsity metric** defined as how similar a social media claim is to a synthetic one. Convert this into a binary prediction:
Prediction = {likely fake, likely NOT fake} if similarity score $$s > / \leq \tau $$
That way, following scores could be computed:
- **True positives:** # claims predicted as likely fake that are actual fakes
- **True negatives:** # claims predicted as likely NOT fake that are not fakes
- **False positives:** # claims predicted as likely fake that are not fakes
- **False negatives:** # claims predicted as likely not fake that are fake


#### Metrics
- Precision
- Recall 
- MCC