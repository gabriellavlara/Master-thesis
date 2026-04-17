# Narrative
5. Results
5.1 RQ1: Semantic Alignment Analysis
    5.1.1 Overview
          - Summary table (mean cosine + BERTScore per LLM)
          - Boxplot distributions per LLM
          - UMAP three-panel (for intuition?)
    5.1.2 Cross-Label Analysis  
          - Table: max/q75/mean BERTScore per LLM per label
          - Boxplot per label (cosine + BERTScore)
          - Kruskal-Wallis + Dunn's test 
	          - H0: BERTScore distributions for FALSE, TRUE and OTHER come from the same population
	          - H1: at least one group has a different distribution
	          - if H1, Dunn's test: which specific pairs of groups differ from each other --> focus on FALSE vs. TRUE
          - KEY FINDING: FALSE > TRUE across all models
- subsection for error analysis: differences between valid. and test set; explain differences/errors in dataset --> 
- curate news for curated dataset. --> use evidence column as base
- decide how to structure the two results (from both datasets)
5.2 RQ2: Disinformation Flagging Performance
    5.2.1 Label Composition Funnel
          - Table: base rate → retrieval → reranking
          - Lift barplot
          - Chi-square on flagged distribution
	          - H0: label distribution among flagged posts matches the random distribution ( considering class imbalance)
	          - H1: the label distribution deviates from random distribtuion
	          - basically checks if my pipeline is **doing what it's supposed to do towards false posts** (hopefully yes?)
          - KEY FINDING: FALSE enriched ~1.7x, TRUE suppressed
    5.2.2 Pipeline Performance
          - Precision@k (top-10% and/or top-25%? How to justify? )
          - nDCG per query averaged
          - Comparison vs **BM25 baseline** (should this be my baseline)
          - Precision-recall tradeoff curve

5.3 Cross-RQ Insights (???) --> in discussion
    5.3.1 Model Comparison
          - RQ1 scores vs RQ2 precision divergence
          - Open vs closed models finding
    5.3.2 Qualitative Analysis → appendix reference
    for the best setting, subset 30-50 generations; error labels; repetitions; out of scope

Labels overlap heavily in semantic space
    → task is hard, individual scores are label-agnostic
        → yet retrieval implicitly enriches for FALSE posts
            → LLM fakes cluster near human disinformation at corpus level
                → this implicit discrimination motivates RQ2:
                  can it be operationalized for detection?
## 5.1.1

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
###  Gemini was excluded as a generator:  
Even with safety settings turned off (so HarmCategory.HARM_CATEGORY_HATE_SPEECH: HarmBlockThreshold.BLOCK_NONE, HarmCategory.HARM_CATEGORY_DANGEROUS_CONTENT: HarmBlockThreshold.BLOCK_NONE), it still failed in generating complete Tweets. This is consistent to gemini's safety alignment, 
**the more safety-tuned a model is, the worse it performs as a fake generator for your framework**:
- Hard blocks (Gemini)
- Soft degradation of output quality (GPT)
- GPT (even without explicit safety refusal) tends to produce more **neutral, balanced, journalistic** text by default — which would push embeddings closer to HUMAN_TRUE than HUMAN_FALSE
- GPT may be **over-following** the article content, producing semantically faithful summaries with a fabricated claim tacked on, rather than fully disinfo-flavored posts
- DeepSeek may have less "helpfulness" bias baked in, producing more raw, emotionally charged outputs that naturally align with HUMAN_FALSE style
### DeepSeek generations exhibit higher overall scores 
(BERTScore and cosine similarity) between (LLM_FALSE, HUMAN_FALSE) than (LLM_FALSE, HUMAN_TRUE/OTHER). And it makes it in a way that could potentially be separable/used as a threshold. ==this is only valid for promptID=6**

- observed result for LLM=DeepSeek, embedding = Gemma
![[promptID=6_llm=deepseek_embedding=gemma.png]]
But that CANNOT be observed for GPT. result for LLM=GPT, embedding = Gemma
![[promptID=6_llm=gpt_embedding=gemma.png]]
### Different LLMs need different levels of prompt specificity to approximate stylistic/linguistic properties of human-authored disinformaiton
_different LLMs require different levels of prompt specificity to approximate the stylistic and linguistic properties of human-authored disinformation._ GPT defaults to a journalistic register unless explicitly constrained, while DeepSeek drifts toward opinion/humor framing. That's a substantive contribution about the **generative capacities** of LLMs — which is literally your thesis title.
**analysis table:**
- Mean subjectivity score per LLM per promptID
- Compared against mean subjectivity of HUMAN_FALSE as a target baseline
- Shown across your embedding similarity results
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

Not only "can synthetic fakes serve as proxies" but "under what conditions and for which misinformation types."

While the pipeline was not designed as a classifier, the retrieval results show a tendency to flag posts that are opinionated, conspiratorial, or potentially misleading, suggesting that semantic similarity to LLM-generated disinformation narratives acts as a weak proxy for harmful content.