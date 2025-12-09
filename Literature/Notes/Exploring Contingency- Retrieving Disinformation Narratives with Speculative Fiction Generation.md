[[EACL__Narrative_Retrieval.pdf]]
#LLMs-as-generators 

- Retrieving texts by their implicit meaning within the domains of disinformation and propaganda detection -> 
	- Couldn´t comprehend *intent*
- Computational hermeneutics: science of interpretation. For an AI to grasp disinfo, it needs to understand that meaning isnt fix. The context shifts the meaning
- **HyDE**: give the LLM a premise; it creates n hypothetical documents **ideal targets** and then finds top-k matches with incoming data batch
	- synthesis beats high number of samples bc it gets more the context
- Pipeline:
1. Input narrative - key premise derived from a dataset´s label taxonomy as the input query
2. Dynamic few-shot sampling: Collect example pairings between input narrative and corresponding texts from the knowledge base
3. Generate hypothetical documents (HyDE): conduct "thought-experiments" based on the input premise and generate n new documents 
- premise - thought experiments - media: source 
1. Dense retrieval and result merging: 
2. Return results: 
- Metrics:
	- narrative contingency: 
	- narrative variance: overall spread 
Narratives with high contingency and variance are harder to retrieve using AI.
- Safety-aligned LLMs did not generate false narratives; so they tested with safety removed models or unsafe models. **Result: removing safety**
- Conclusion: simpler, more superficial text is higher to identify; complex denial needs complex interpretation
### Main takeaways for my work:
How did they compare narratives? Used sentence embeddings using **gte-large**. Each sentence has a set of text embeddings. They calculate the centroid of all text embeddings associated to a narrative, 
They measure **narrative distinctness, contingency and variance** 
- Useful to check out: possible correlation between results on readability metrics between texts with and without misinformation
- 