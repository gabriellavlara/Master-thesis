#LLMs-as-generators 
[[genLLM-automated-factchecking.pdf]]

- Fact-checking: verifying truthfulness of a given claim:
	- Fact Verification: assess veracity of a given claim or a few sentences
	- **Fake News Detection: check trustworthiness of longer texts, f.e. news articles**
	- Evidence retrieval: Gather information from trusted sources to assess veracity of claims
	- **Claim detection: identify claims containing verifiable information necessitating verification (check-worthy or verifiable)**
	- Previously fact-checked claims detection
### Synthetic data generation
- LLMs employed to create entire datasets or their parts, which is used for training or fine-tuning -> useful when there is unavailable or limited dataset for specific tasks or languages
- Augments datasets by filling gaps in underrepresented categories or increasing variability
- Prompting: set of techniques used to improve the performance of LLMs by designing the instructions
	- To reduce ambiguities, it is essential to define all relevant terminology within the prompt, e.g., the attributes of check-worthy claims.
	- Prompt structure and wording can influence LLM performance. Some techniques include **role-specification** and JSON formatting
	- **Few-shot prompting:** model provided with multiple in-context examples, enhancing LLMs understanding of the task -> in context examples useful in claim generation (Kamoi et al., 2023b; Li et al., 2023a); decomposing input text into sub-claims helps 
	- **Chain-of-thought:** technique that leverages reasoning abilities by incorporating intermediate steps before generating predictions. 