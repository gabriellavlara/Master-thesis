# Next Steps (Breadcrumbs)
### 30.01.26
- GET BETTER DATASET!!!
- try with different embedding models. F.e. try with OpenAI's embedding model? Just to see if it captures any other aspects
- try new prompting techniques that explicitly mention the tweet must sound like it was written by a human.
- implement quantitative metrics to evaluate results:
	- precision@k 
	- TPR 
### 24.01.26
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
### 9.01.26
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
- ==**Implement embeddings step **== ✅

- Start experimenting in the MTEC server. Access information can be found in .env file
-  Restructure pipeline into 5 steps? Check [[Methodology-pipeline.canvas|Methodology-pipeline]]

### 15.12.25
1. Auto save in LIST OF DICTS whenever i call run_llm function --> waaay more efficient ✅
2. Decide how to store information if ONE prompt generates TWO tweets -> should each be stored in a diff row? Yes, if possible. ✅
3. Write AUTO SAVING in jsonl files to make sure info is not lost even after kernel is disconnected --> or parquet files ✅
4. ==Scale it a bit. Run f.e. each prompt variation (let's say i'll have 10) with a different model (I have 3 for now) and with different versions of the news article (2, for now) and different n_shots (0,1). In total, would be 120 generated instances?== ✅


- **Ideas**:
Evaluate different prompts given fluency, quality, adequacy, coherence, "human-likeliness", correctness, naturalness, hallucination, "consistency" --> could do that by prompting another LLM to evaluate on those aspects. 

Number of character diff, semantic similarity

Define "disinformation"-traits (f.e. numerical fabrication, change in associated people)

  
### 05.12.25
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
### 28.11.2025
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

