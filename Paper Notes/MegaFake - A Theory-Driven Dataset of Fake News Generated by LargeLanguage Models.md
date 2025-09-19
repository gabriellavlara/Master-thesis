#paper #generated #fakenews 

*link*: https://arxiv.org/pdf/2408.11871

- Main idea: generated fake news dataset **MegaFake** built on top of GossipCop dataset
    - Motivation: build benchmark to train/test detectors
- Detecting fake news: content- (analyse linguistic elements, such as syntax and semantics) vs. context based (propagation patterns of news articles) approach
- Categories of LLM-generated info:
    - **Style based fake** → Sheep´s clothing: rewrite an article with a sensational tone OR rewrite fake news article with objective and neutral style
    - **Content based fake** → manipulate by modifying multiple attributes
    - **Integration based fake** → information blending: integrate fake and legitimate news for creating new fake content
    - **Story based fake** → Narrative generation: generate fake from a certain message (given a title, create a false news)
    - **Style based legitimate** (polish legitimate news)
    - **Integration based legitimate** (synthetize two articles into one)
- Intentional fake != hallucinations or unintentional fakes
- **Binary fake news classifier**
	- NLGs (LLaMa, ChatGLM, GPT4, Claude, etc) evaluated on MegaFake and GossipCop datasets; some are finetuned
	- NLUs (BERTint, RoBERTa, DeCLUTR, etc) fine-tuned for fake news detection
 - ### Conclusion#
	- NLU (Natural Language Understanding) models outperform NLG (Natural Language Generator) models in detecting LLM-gen fakes
	- Larger models without fine-tuning are prone to overfit the dominant class -> predisposed to favor most frequent class --> *NLG have higher number of false positives*
	- Smaller models without finetuning perform fine
	- Cross-experiments: neither model could effectively learn latent features from one category of fake (f.e. organic) and apply them to detect another type (f.e. synthetic)
- ### Limitations
	- real-world scenarios demand multi-label classification: propaganda, click-bait, satire, conspiracy
	- 
	
![[megafake-pipeline.png]]![[MegaFake.pdf]]