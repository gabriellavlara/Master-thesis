1. Testing my pipeline without vs. with **claim-detection** step.
Basically what this step did was use TextBlob to check the subjectivity of a 


| LLM      | Embeding | k   | Subjectivity threshold | Precision@k | Mean BERTScore F1 | Opinion contamination rate | Recall@k |
| -------- | -------- | --- | ---------------------- | ----------- | ----------------- | -------------------------- | -------- |
| DeepSeek | Gemma    | 25  | 0.5                    | 0.233766    |                   |                            | 0.052786 |
| DeepSeek | Gemma    | 25  | 0.75                   | 0.256198    |                   |                            | 0.047898 |
| DeepSeek | Gemma    | 25  | 1 (no claim detection) | 0.261411    |                   |                            | 0.061584 |
| GPT      | Gemma    | 25  | 0.5                    |             |                   |                            |          |
| GPT      | Gemma    | 25  | 0.75                   | 0.207627    |                   |                            | 0.047898 |
| GPT      | Gemma    | 25  | 1 (no claim detection) | 0.205021    |                   |                            | 0.047898 |
|          |          |     |                        |             |                   |                            |          |
|          |          |     |                        |             |                   |                            |          |
| DeepSeek | Gemma    | 50  | 0.5                    | 0.280702    |                   |                            | 0.109482 |
| DeepSeek | Gemma    | 50  | 0.75                   | 0.280093    |                   |                            | 0.118280 |
| DeepSeek | Gemma    | 50  | 1 (no claim detection) | 0.269142    |                   |                            | 0.113392 |
| GPT      | Gemma    | 50  | 0.5                    |             |                   |                            |          |
| GPT      | Gemma    | 50  | 0.75                   | 0.248175    |                   |                            | 0.099707 |
| GPT      | Gemma    | 50  | 1 (no claim detection) | 0.240196    |                   |                            | 0.095797 |
|          |          |     |                        |             |                   |                            |          |
|          |          |     |                        |             |                   |                            |          |


# What result techniques should i use?
## RQ1: Semantic similarity between LLM-generated and human-authored disinformation
This is answered **before** the flagging pipeline — it's about the quality of LLM generation itself.
**Relevant metrics:**
- **BERTScore F1** between LLM-generated posts and human FALSE posts — directly measures semantic similarity
- **Cosine similarity** from your embedding model — same idea, different angle
- **Distribution of scores**: do LLM posts cluster close to human FALSE posts, or are they far apart?
## RQ2: Synthetic fakes as proxies for flagging false posts

This is answered **by** the flagging pipeline, and is your main experimental result.

**Relevant metrics:**

- **Precision@k** — are the posts flagged by LLM similarity actually FALSE? This is your direct answer
- **Opinion contamination rate** — shows the pipeline isn't just retrieving any similar post, but specifically false claims
- **Label distribution of flagged posts** — what mix of TRUE/FALSE/OTHER gets flagged?
- **Claim detection ablation** — shows that refining the pipeline further improves proxy quality

RQ1 is a **prerequisite** for RQ2. The argument flows as:

> _"LLMs can generate semantically similar disinformation (RQ1, shown by BERTScore/cosine), and because of this similarity, they can serve as proxies to surface false human posts (RQ2, shown by Precision@k)_