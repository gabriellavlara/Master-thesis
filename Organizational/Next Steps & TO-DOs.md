# Next Steps (Breadcrumbs)
### 15.12.25
1. Auto save in LIST OF DICTS whenever i call run_llm function --> waaay more efficient
2. Decide how to store information if ONE prompt generates TWO tweets -> should each be stored in a diff row? Yes, if possible.
3. Write AUTO SAVING in jsonl files to make sure info is not lost even after kernel is disconnected
4. Scale it a bit. Run f.e. each prompt variation (let's say i'll have 10) with a different model (I have 3 for now) and with different versions of the news article (2, for now) and different n_shots (0,1). In total, would be 120 generated instances?
- Idea:
Evaluate different prompts given fluency, coherence, --> could do that by prompting another LLM to 
  
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
	- cost_estimate
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

# TO-DOs 
```tasks
not done


```

