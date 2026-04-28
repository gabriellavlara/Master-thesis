- topic coverage! my generations are only ever about the news articles i input. 
1. BERTScore is not the best technique to flag disinformation posts, and it usually gives higher scores between (HUMAN_TRUE, LLM_FALSE)
- compliance! Different LLMs comply differently.
	- even tho i DEACTIVATED safety alignments for gemini with, it still was the model that least complied. GPT complied moderately, and DeepSeek complied the most! 
```
```safety_settings = {
HarmCategory.HARM_CATEGORY_HARASSMENT: HarmBlockThreshold.BLOCK_NONE,
HarmCategory.HARM_CATEGORY_HATE_SPEECH: HarmBlockThreshold.BLOCK_NONE,
HarmCategory.HARM_CATEGORY_SEXUALLY_EXPLICIT: HarmBlockThreshold.BLOCK_NONE,
HarmCategory.HARM_CATEGORY_DANGEROUS_CONTENT: HarmBlockThreshold.BLOCK_NONE,
}```


It remains unclear whether the observed overlap reflects a limitation of BERTScore as an evaluation metric for disinformation similarity, or whether it indicates that current LLM-generated fakes do not yet fully replicate the semantic characteristics of human-authored disinformation. Future work could address this by evaluating alternative similarity metrics or conducting human judgment studies.

Examples:
for LLM=deepseek, EMBEDDING=gemma
![[Pasted image 20260305141944.png]]
2. 