## Base test
### Data curation
Problems: 
1. Veracity labels have no explanation -> it's not clear whether they are true/false, and on some occasions that i have manually looked for its truthfulness online, many of them were not true --> new LLMs might have information on that. 
2. A lot of the tweets are not really relevant and are very far off the political news event. F.e. for the Charlie Hebdo case, one shares the post of an art released by artist Banksy. So it's very mixed and not really all related directly to the shooting. --> maybe later filter out subsets of examples 
3. No direct news event associated. So f.e. I have to manually curate a set of real news articles that describe the event. This is one issue i had not thought about before, that maybe one news event R should have a set of news articles? And if that's the case, what is a good measure to choose that? --> probably giving full articles will minimize variation of what i get (), might increase quality 
FOLLOW UP QUESTION: does it get MORE creative if i add more information to the prompt? Or less?

### Data generation
1. Very slow generation. For one input, even when using mac's inbuilt GPUs, it takes around 5minutes for ONE response with Gemma2b and way longer with Qwen. That DOES NOT scale well. 
2. Trade-off between **instruction-tuned** and **base** language model:
- +: base model has no safety filters and has more space for creativity 
- -: demands very specific prompting style and doesn't allow implementation of promtping techniques properly (f.e. persona-based or chain-of-thought)
Data-backed up decisions as to why i would continue with IT models

Proprietary models: start with GPT and DeepSeek. First start with something that works, 
1. Run LLM locally or access through API?

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




