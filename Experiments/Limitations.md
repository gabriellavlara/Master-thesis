1. BERTScore is not the best technique to flag disinformation posts, and it usually gives higher scores between (HUMAN_TRUE, LLM_FALSE)
It remains unclear whether the observed overlap reflects a limitation of BERTScore as an evaluation metric for disinformation similarity, or whether it indicates that current LLM-generated fakes do not yet fully replicate the semantic characteristics of human-authored disinformation. Future work could address this by evaluating alternative similarity metrics or conducting human judgment studies.

Examples:
for LLM=deepseek, EMBEDDING=gemma
![[Pasted image 20260305141944.png]]
2. 