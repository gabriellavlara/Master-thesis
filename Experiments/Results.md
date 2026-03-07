# Quantitative 
1. Testing my pipeline without vs. with **claim-detection** step.
Basically what this step did was use TextBlob to check the subjectivity of a 


| LLM      | Embeding | k   | Subjectivity threshold | Precision@k  | Mean BERTScore F1 | Opinion contamination rate | Recall@k |
| -------- | -------- | --- | ---------------------- | ------------ | ----------------- | -------------------------- | -------- |
| DeepSeek | Gemma    | 25  | 0.5                    | 0.233766     |                   |                            | 0.052786 |
| DeepSeek | Gemma    | 25  | 0.75                   | 0.256198     |                   |                            | 0.047898 |
| DeepSeek | Gemma    | 25  | 1 (no claim detection) | **0.261411** |                   |                            | 0.061584 |
| GPT      | Gemma    | 25  | 0.5                    | **0.251208** |                   |                            | 0.050831 |
| GPT      | Gemma    | 25  | 0.75                   | 0.207627     |                   |                            | 0.047898 |
| GPT      | Gemma    | 25  | 1 (no claim detection) | 0.205021     |                   |                            | 0.047898 |
|          |          |     |                        |              |                   |                            |          |
|          |          |     |                        |              |                   |                            |          |
| DeepSeek | Gemma    | 50  | 0.5                    | 0.280702     |                   |                            | 0.109482 |
| DeepSeek | Gemma    | 50  | 0.75                   | **0.280093** |                   |                            | 0.118280 |
| DeepSeek | Gemma    | 50  | 1 (no claim detection) | 0.269142     |                   |                            | 0.113392 |
| GPT      | Gemma    | 50  | 0.5                    | **0.262873** |                   |                            | 0.094819 |
| GPT      | Gemma    | 50  | 0.75                   | 0.248175     |                   |                            | 0.099707 |
| GPT      | Gemma    | 50  | 1 (no claim detection) | 0.240196     |                   |                            | 0.095797 |
|          |          |     |                        |              |                   |                            |          |
|          |          |     |                        |              |                   |                            |          |

# Qualitative
1. Gemini was excluded as a generator:  Even with safety settings turned off (so HarmCategory.HARM_CATEGORY_HATE_SPEECH: HarmBlockThreshold.BLOCK_NONE, HarmCategory.HARM_CATEGORY_DANGEROUS_CONTENT: HarmBlockThreshold.BLOCK_NONE), it still failed in generating complete Tweets. This is consistent to gemini's safety alignment, 
**the more safety-tuned a model is, the worse it performs as a fake generator for your framework**:
- Hard blocks (Gemini)
- Soft degradation of output quality (GPT)
- GPT (even without explicit safety refusal) tends to produce more **neutral, balanced, journalistic** text by default — which would push embeddings closer to HUMAN_TRUE than HUMAN_FALSE
- GPT may be **over-following** the article content, producing semantically faithful summaries with a fabricated claim tacked on, rather than fully disinfo-flavored posts
- DeepSeek may have less "helpfulness" bias baked in, producing more raw, emotionally charged outputs that naturally align with HUMAN_FALSE style
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