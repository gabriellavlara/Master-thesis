# Goals:
1. Does the pipeline run end-to-end?
2. Do prompts actually induce measurably false content? Are different prompt variants _meaningfully different_?
3. Do embeddings distinguish article vs generated tweet in any signal at all?
4. Do embeddings show false content (organic AND synthetic) closer to each other than real and fake?

### Data curation
#### **Information:**
- Sample dataset: ComplexDataLab/Misinfo_Datasets
- News event: Charlie Hebdo shooting (2015)
- Platform: Huggingface
- link of subset: [https://huggingface.co/datasets/ComplexDataLab/Misinfo_Datasets]
- original link of PHEME dataset: [https://figshare.com/articles/dataset/PHEME_dataset_for_Rumour_Detection_and_Veracity_Classification/6392078]
- Number of posts: 
	- true 193 
	- unverified 149 
	- false 116
#### **Problems:** 
1. Veracity labels have no explanation -> it's not clear whether they are true/false, and on some occasions that i have manually looked for its truthfulness online, many of them were not true --> new LLMs might have information on that. 
2. A lot of the tweets are not really relevant and are very far off the political news event. F.e. for the Charlie Hebdo case, one shares the post of an art released by artist Banksy. So it's very mixed and not really all related directly to the shooting. --> maybe later filter out subsets of examples 
3. No direct news event associated. So f.e. I have to manually curate a set of real news articles that describe the event. This is one issue i had not thought about before, that maybe one news event R should have a set of news articles? And if that's the case, what is a good measure to choose that? --> probably giving full articles will minimize variation of what i get (), might increase quality 
FOLLOW UP QUESTION: does it get MORE creative if i add more information to the prompt? Or less?

### Data generation
#### **Information**
- Models: GPT-4o-mini and Deepseek-chat
- 75 generated instances in generations.jsonl
#### **Problems**
1. Very slow generation. For one input, even when using mac's inbuilt GPUs, it takes around 5minutes for ONE response with Gemma2b and way longer with Qwen. That DOES NOT scale well. 
2. Trade-off between **instruction-tuned** and **base** language model:
- +: base model has no safety filters and has more space for creativity 
- -: demands very specific prompting style and doesn't allow implementation of promtping techniques properly (f.e. persona-based or chain-of-thought)
Data-backed up decisions as to why i would continue with IT models

Proprietary models: start with GPT and DeepSeek. First start with something that works, 
1. Run LLM locally or access through API? For now, am only testing with API access -> result tends to be much better
   - for future, might want to test with fine tuned LMs for tweet generation.

| Criterion                         | API LLM     | Local LLM        |
| --------------------------------- | ----------- | ---------------- |
| Speed                             | ⭐⭐⭐⭐⭐       | ⭐⭐               |
| Cost                              | $ per token | Free after setup |
| Setup                             | Easy        | Hard             |
| Safety filters                    | Yes         | None             |
| Privacy                           | Medium      | High             |
| Model quality                     | Very strong | Medium           |
| Reproducibility                   | Good        | Very good        |
| Scalability                       | Excellent   | Poor             |
| Good for misinformation research? | Not ideal   | Excellent        |
| Testing prompting strategies?     | Excellent   | Not ideal        |

### Evaluation methods
For generations:
- I have very subjective metrics. Need to define more objective ones to properly evaluate it (f.e. is this tweet objectively false? Is this potentially dangerous? etc)

# Problems & Improvements 
- [ ] Write a "status update" functionality for my generation code 
- [ ] Also add eventID to the generation json maybe? or not, just store it on different names
- [ ] Restructure the folders to have one probably called scripts/generate.py
- 