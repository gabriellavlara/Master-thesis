## Thesis TODO: Prioritized


### Tier 1: Essential (must do)
- [x] **Flagging technique**: pick percentile-based top-X% (e.g. top-10% and top-25%), report both, move on ✅ ✅ 2026-04-24
- [ ] ==Preprocess text: remove URL from the human posts? Not sure!
- [x] **RQ1 results**: cross-group similarity comparison (BERTScore boxplots per label, per LLM) ✅ 2026-04-30
- [ ] **RQ2 results**: precision@k / precision@x% on flagged human posts + nDCG
- [x] ==**BM25 baseline**==: implement retrieval lift and precision@k for BM25, compare against your pipeline (supervisor recommended) ✅ ✅ 2026-04-24
- [ ] **Writing**: results section, discussion section, finish theoretical gaps


### Tier 2: Important but scopeable
- [ ] **Stability analysis**: std of BERTScore over rep_index per (promptID x articleID) — one table, half a day --> just add this to the results table, no need for a separate section
- [ ] **Roberta-large BERTScore**: run as robustness check alongside BERTWeet, confirm relative rankings hold --> just take roberta (**xlmr** --> modern roberta model. (check))
- [ ] **Subjectivity Analysis**: show some examples of pairs of LLM generated instances vs. human generated text and their respective scores.

### Tier 3: Nice-to-have (cut if time is short)
**BLEURT / MoverScore**: additional similarity metrics — adds complexity without changing core findings, acknowledge as future work instead --> only if i have time 
- [ ] **UMAP/PCA visualization**: embedding space plot showing LLM_FALSE near HUMAN_FALSE — only if interpretable and done in half a day --> density kernels; 
- [ ] **More prompting techniques**: entity framing, political bias prompts — rerunning everything is weeks of work; frame current 4 prompts as proof-of-concept and move remaining strategies to limitations/future work section --> ==hero/villain framing==. 
### Ongoing
- [ ] **Supervisor communication**: explicitly discuss prompting scope tradeoff given timeline — get alignment on what is "enough" 

# Next Steps (Breadcrumbs)
## 27.03
- ==**Scale Data Generation (Priority: High) **== ✅
	- Select **one fixed experimental setup**:
	    - 1 LLM (e.g., best-performing so far)
	    - 1 embedding model
	    - 1–2 prompt types (e.g., fabrication + misrepresentation)
	- Increase number of generated samples:
	    - Run pipeline multiple times **OR**
	    - Generate multiple posts per article
	- Target: **~100–300 LLM-generated posts per setup**
- --> ==**Evaluate Stability of Results**== 
	- Re-run full pipeline with expanded dataset
	- Compute:
	    - precision@k (and/or @x%)
	    - label distribution in top-k / top-x%
	- Compare results across runs:
	    - mean and standard deviation
	    - check for consistency in trends (e.g., enrichment of HUMAN_FALSE in top tail)
	- Goal: verify whether observed behavior is **stable or due to randomness**
- Test other prompt variations: **READ ENTITY FRAMING PAPER**
	-  **entity framing centered prompt (hero/villain)**
	- **conspiracy theory**
	- **propaganda techniques** 
	- NotebookLM the three papers on propaganda before prompting under "propaganda"
-  Test BLEURT and MoverScore as further metrics for semantic similarity 🤔
	- to which RQ does it support most? I can say it is a complementary metric for RQ1 mb? 
	- (*bonus*: optional robustness checks), otherwise just mention it as future work. 
	- BLEURT: regression metric fine tuned on human judgment 
	- MoverScore: embedding metric that captures similarity despite different sentence structures (captures paraphrases etc.)
- **Mann-Whitney U test for RQ1** --> can only do that after i have generated MORE instances of false posts per llm
- ==**Human vs. LLM semantic alignment**==: compare human and llm false posts to a human_false_centroid --> can only do that after i have generated MORE instances of false posts per llm
## 20.03
- **Chi-square test for RQ2** ✅
- ==Add nDCG@k as supporting metric== --> are false posts ranked higher overall  ✅
- Write baseline of the results section :)  ✅

## 13.03
- URGENTTTTTT: Complete Gemini 2.5 Flash generations by rerunning the 5 missing combinations (articleID=9 for all 4 promptIDs, and articleID=8 for promptID=10) after the daily quota resets, with a 12-second delay between API calls to avoid hitting the RPM limit. ✅
- Test the following hypothesis: "safety alignment inversely correlates with semantic fidelity to human disinfo."✅
	- Finish setting up Qwen, and set up Llama with promptIDs= {6,7,9, 10} ✅
	- Fix BERTSCore function; max tokens ✅
	- Add max character constraint to prompt ✅
	- Scale up to 20 generated instances per promptID
- Write in the methodology a bit more about limitations and design choices i chose.
	- News article;
	- Prompting techniques i have tried and what i found out
- Finish notebook to RQ1 and do notebook for RQ2 ✅
## 6.03
-  Analyse class differences
	- task: run TF/IDF to capture most characteristic terms per class; measure overlap between (HUMAN_FALSE, LLM_FALSE) and (HUMAN_OTHER, LLM_FALSE).
	- hypothesis: `LLM_FALSE` may currently overlap more strongly with `HUMAN_OTHER` due to stylistic/emotional similarity, and not claim-similarity
	- motivation: understand **if my retrieval system is based on topic similarity / stylistic similarity / discourse (stance/claim) type similarity **
-  Introduce **claim-type-awareness** in my pipeline (fact vs. opinion)  ✅
	- task: introduce a mechanism to differentiate factual / verifiable claims VS. opininon/humor/comment --> intermediate step somewhere in my pipeline
	- new proxy based disinfo detection will consist of:
	- inform myself about VADER sentiment analysis
	a. retrieval of m candidates via cosine similarity
	==b. claim-type filtering (retain only factual claims)==
	c. reranking via BERTScore
	- some candidate approaches: pre-trained check-worthiness/claim detection model; LLM-as-a-judge
-  Experimental validation plan: ✅
	- task: rerun precision, recall, f1 for that and check if precision increased! 
- Read papers Veronika sent me; read about other scoring techniques
## 27.02
- Evaluate qualitatively WHAT makes the posts so similar to each other.
	- Perform HUMAN-only analysis: identify linguistic differences between HUMAN_FALSE and HUMAN_TRUE (f.e. )


- Write methodology pipeline: ✅
	- Retrieval–reranking design ✅
	- Explanation of top-k evaluation
	- Math formulations for generations and embedding parts. 

- Write a results.py that i can rerun anytime. It should ✅
	- load all parquets
	- merge results with human_ and llm_posts 
	- create **run_summaries.parquet**
	- produce base plots with stats like bertscore and cosine similarity for each combination of models
- Change S-BERT to another model (RoBERTa or MPNET) ✅
## 13.02.26
- **==RETRIEVE & RERANK PIPELINE==**: first filter based on cosine similarity (f.e. threshhold would be similarity > 0.5), then compute BERTScore for all remaining entries. ✅
	- Why? BERTScore is way more computationally expensive
	- Also makes sense to remove completely misaligned (f.e. topic misaligned) values from the comparison
- Implement BERTScore in addition to cosine similarity.✅
	- **Cosine similarity** → “Are these posts about similar things?”
	- **BERTScore** → “Do these posts make similar claims using similar language?”
	- BERTScore can penalize mismatched tokens more than a single sentence embedding might
	- **My hypothesis: BERTScore will increase separation between HUMAN_FALSE and HUMAN_TRUE compared to cosine in embedding space.** --> KINDA YES!

- Improve `RUN_DISINFORMATION_DETECTION` script ✅
    - produce results **per experimental setup** (for each `HUMAN_` post):
        - `datasetID` _(add this — otherwise you’ll mix datasets later)_
        - `embedding_model`
        - `similarity_metric`
        - `llm_model`
        - `promptID`
- Results table for each combination of EMBEDDING_MODEL, LLM_MODEL -> the similarity and flagging should be all in the same result table. ✅
    - store instance-level score table to disk ✅
        - prefer **Parquet** for size + speed; CSV ok for small tests
        - file name should encode dataset + embedding model + metric (or store all in one tidy file)
- Improve evaluation script
    - per setup (embedding_model × metric × llm_model × promptID), compute summary table:
        - `n, mean, median, std, q25, q75`
    - write `closeness_summary.csv` → thesis-like results table
- Implement flagging + prediction metrics
    - implement flagging rules **per setup** (don’t mix prompts/models):
        - threshold-based on `score_to_llm_false`
        - top-k (define clearly if it’s top-k per LLM_FALSE seed or top-k by human score)
    - compute confusion matrix (choose evaluation labels):
        - treat `HUMAN_FALSE` as positive class
        - exclude or separately report `HUMAN_OTHER` _(decide and document)_
    - compute and store:✅
        - `precision, recall, F1`
        - also store `TP, FP, TN, FN` _(makes debugging easy)_
        - store `n_flagged` + `flag_rate` _(very useful for interpretation)_
    - save as `flagging_metrics.csv`
    - note in thesis: metrics may be poor initially → use as motivation for next prompt iteration
    
## 3.02.26
- update slides with new dataset 
	- find out how to extract more "general" conclusions from the results? Even if intermediate --> **results table that evaluate per experimental setup ;)**
	- create wizmap maybe?
- Run pipeline with better dataset: Monkeypox misinformation (https://www.kaggle.com/datasets/stephencrone/monkeypox) ✅
- try new prompting techniques that:
	- explicitly mention the tweet must sound like it was written by a human ✅
	- provide examples (few shot prompting)
	- explicitly mention the disinformation type: ✅
		- **fabrication, false attribution, inaccurate numerical quantities, misrepresentation**)-> from paper fighting fire w fire 
		- **Style-based, content-based, information-blending, story-based** —> from Megafake paper 
	
## 30.01.26
- apply PCA before UMAP -> to denoise (apparently that's best practice)
- Inform myself about other embedding models: --> make a table with (what they capture, typical models, known limitations on short texts (tweets))
    - _Event / semantic embeddings_ --> [[sentence-bert.pdf]] ✅[[Its_All_in_the_Embedding_Fake_News_Detection_Usin.pdf]] ✅
    - _Style / grammar embeddings_ --> [[autorship_attribution_for_text_generationpdf.pdf]] ✅
    - _Stance / sentiment embeddings_ --> [[detecting_stance_in_tweets.pdf]]
- Write a bit in the methodology page on overleaf 

## 24.01.26
- Implement embedding storage ✅
- write these steps as functions in a .py file, and then have them all be easily run in src/embedding.py file. ✅
- Prepare some slides on the parts of the pipeline i've implemented until now, problems i've encountered and what could be observed (VERY PREMILINARY) 
- produce a **tidy results table**: ✅
	- define score: max cosine similarity to any LLM_fake
	- columns: post_id, event_id, label (true/false), score, top_k_neighbor_ids, neighbor_labels, generator_config_id, embed_model_id
	- deliverable: results.csv
- integrate **human evaluation**: ✅
	- *Which stylistic constraints make LLM fakes behave more like human fakes?* 
	- clean and normalize generations_score.json
	- join generation scores with embedding behaviour (maybe? )
	- deliverable: just add a section in 02_llm_generation.ipynb
- **prompt/style ablation analysis**: ✅
	- *Which prompts generate the most human-alike posts?*  
	- link human evaluation of prompts to actual embedding results (Check if my perceived human_likeness equals to avg_sim_to_human_posts)
	- deliverable: 04_results_inspection.ipynb
## 9.01.26
- **Evaluate first results of the generations (sanity check)**
1. Manual inspection: ✅
	Sample 15-20 instances and see if
	- Is it clearly about the correct event?
	- Does it _contain_ a false or misleading claim?
	- Is the false claim:
	(a) subtle / plausible
    (b) obviously wrong / absurd
	- Would a human plausibly post this on social media?
	- Any catastrophic failures? (wrong event/wrong location/impossible facts)
	==problem: subjective metrics. Improve them for the next run==

2. Automated control metrics. -> not for now
	**Manual (0–2 each):**
	- **Human-likeness** (reads like a real tweet?)
	- **Event relevance** (clearly about the article/event?)
	- **Fabrication quality** (plausible false claim vs random nonsense?)
	- **Coherence/fluency** (grammar, clarity, no weird structure)
	- **Constraint compliance** (includes at least one confident false claim?)
	https://www.digitalocean.com/community/tutorials/automated-metrics-for-evaluating-generated-text 
	**Automatic:**
	- **Length / character count** (<= 280)
	- **Basic formatting stats** (hashtags, mentions, URLs count; optional)
- Run basic analytics for the evaluation metrics of the first 75 generated instances. 
	- Might be interesting to know: which prompt generated the best result (with the highest overall score)? Which prompt generated the most tweet-like and/or human-like entry?
- ==**Implement embeddings step**== ✅

- Start experimenting in the MTEC server. Access information can be found in .env file
-  Restructure pipeline into 5 steps? Check [[Methodology-pipeline.canvas|Methodology-pipeline]]

## 15.12.25
1. Auto save in LIST OF DICTS whenever i call run_llm function --> waaay more efficient ✅
2. Decide how to store information if ONE prompt generates TWO tweets -> should each be stored in a diff row? Yes, if possible. ✅
3. Write AUTO SAVING in jsonl files to make sure info is not lost even after kernel is disconnected --> or parquet files ✅
4. ==Scale it a bit. Run f.e. each prompt variation (let's say i'll have 10) with a different model (I have 3 for now) and with different versions of the news article (2, for now) and different n_shots (0,1). In total, would be 120 generated instances?== ✅


- **Ideas**:
Evaluate different prompts given fluency, quality, adequacy, coherence, "human-likeliness", correctness, naturalness, hallucination, "consistency" --> could do that by prompting another LLM to evaluate on those aspects. 

Number of character diff, semantic similarity

Define "disinformation"-traits (f.e. numerical fabrication, change in associated people)

  
## 05.12.25
- Set up a config file with the API keys: ✅
	- ChatGPT:
		- Provider: openAI
		- Model_name:
		- Default_params:
		- API_key: *** 
	- DeepSeek
		-  Provider: DeepSeek
		- Model_name:
		- Default_params:
		- API_key: *** 
		==*to find API_keys, access the .env file on the GitHub project*==
- Write a function that runs prompt on LLM using API key  ✅
	- def call_model(model_id, system_prompt, user_prompt, **params):
    1. Build the messages list.
    2. Call the API.
    3. Return both raw response + extracted text + metadata.
- Define DF structure for logging generated tweet. It should contain: ✅
	- tweetID
	- eventID
	- news_article-ID
	- provider
	- prompting_strategy
	- system_prompt
	- user_prompt
	- generated_tweet
	- time_to_generate
	- timestamp
	- cost_estimate (check out website and write function that calculates that given n input tokens, output tokens, )
- Set up account on Azure Cloud or Google cloud (free TPU usage. Do i even need it?)
- Mini-evaluation of instruction-tuned vs. base models:
	- pick 10-15 generated examples by each and compare based on tweet likeness, factuality, creativity
## 28.11.2025
- Properly store news_articles as a DF. It should contain: ✅
	- event_id
	- newsarticle_id
	- title
	- headline
	- body
- Try different ways of context for prompting: 
	- Context related strategies
1. giving only title + headline
2. giving title + headline + body
Investigate WHEN does the LLM get more creative?
	- Prompt related strategies
	- "controlled but realistic"
	- "more creative"
	- "left/right oriented"
	- chain-of-thought prompting: first extract claim from news articles, then think about two opposing narratives, and then generate
	
- Start the generation process using LLMs 
1. define prompting strategies 
2. define LLMs to be used (maybe for now, only one or two)
3. decide how to **store the generated instances with metadata**. My suggestion would be to have a DF that associated generated tweet to event_ID and newsarticle_ID and prompting_strategy. 
generation_ID; event_ID newsarticle_ID; 
model_id; [...]

