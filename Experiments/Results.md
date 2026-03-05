1. Testing my pipeline without vs. with **claim-detection** step.
Basically what this step did was use TextBlob to check the subjectivity of a 
|                          |  | With Claim Detection |
|:--------------------------------|:-----------------------:|:--------------------:|
| Precision@k                     | --                      | --                   |
| Opinion Contamination Rate (%)  | --                      | --                   |
| Mean BERTScore F1               | --                      | --                   |

*Results computed at k=___. Precision@k and Opinion Contamination Rate are averaged across all promptIDs (mean ± std).*

| LLM      | Embeding | k   | Subjectivity threshold | Precision@k | Mean BERTScore F1 | Opinion contamination rate |
| -------- | -------- | --- | ---------------------- | ----------- | ----------------- | -------------------------- |
| DeepSeek | Gemma    | 50  | 0.5                    |             |                   |                            |
| DeepSeek | Gemma    | 50  | 0.75                   |             |                   |                            |
| DeepSeek | Gemma    | 50  | 1 (no claim detection) |             |                   |                            |
| GPT      | Gemma    | 50  | 0.5                    |             |                   |                            |
| GPT      | Gemma    | 50  | 0.75                   |             |                   |                            |
| GPT      | Gemma    | 50  | 1 (no claim detection) |             |                   |                            |
|          |          |     |                        |             |                   |                            |
|          |          |     |                        |             |                   |                            |
|          |          |     |                        |             |                   |                            |
|          |          |     |                        |             |                   |                            |


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