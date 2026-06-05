
## Fake News
- [[tutorial-fakenews.pdf]] - definitions of mis-/dis-/malinformation
- [[dataset-of-fakenews-a-survey.pdf]] - definitions of fake news and listing of existing datasets
- [[fakenews-detection-data-mining.pdf]] - fake news characterizations on psychology and social theories + existing algorithms from a data mining perspective
- ==[[rumors-socialmedia.pdf]]== - rumo
- ==[[https://link.springer.com/article/10.1007/s13278-023-01028-5]]== - fake news: definitions and formalities
```dataview
LIST
FROM "Literature/Notes"
WHERE contains(file.tags, "fakenews")
```
## Datasets
- [[fakenewsnet.pdf]] – FakeNewsNet dataset
-  [[MegaFake.pdf]] – dataset of LLM generated fake news and its prompting techniques
- [[all-in-one_PHEMEdataset.pdf]] - automatic resolution of rumor using PHEME and 
- [[disinfo-capabilities-of-LLMs.pdf]]- evaluate 10 LLMs using 20 disinfo narratives
- ==[[guide-to-disinfo-detectin.pdf]]== - 
- ==**HQP dataset** check that out!==

```dataview
LIST
FROM "Literature/Notes"
WHERE contains(file.tags, "datasets")
```
## LLMs as generators
- [[gpt_disinforms.pdf]] - dataset of GPT3 produced synthetic posts and the comparison between synthetic vs. organic fakes vs. truths
- [[generate-first-then-sample.pdf]] - generate LLM fakes + reinforcement learning to set optimal real-to-fake news ratio -> improve classification of fakes
- [[EACL__Narrative_Retrieval.pdf]] - generate fake narratives given a premise + compare them with real ones 
- [[fighting-firewfire.pdf]] - generate dataset of 4 types of misinformation based on a real news event
- [[genLLM-automated-factchecking.pdf]] - survey that summarizes approaches in generative LLMs for automated fact checking
- - [[defending-against-fake-news-GROVER.pdf]] - LLM that GENERATES and identifies fakes \
- [[fighting-firewfire-dual-role-LLMs.pdf]] - pipeline that prompts fakes + eliminate hallucinations + identify fakes from truths using LLMs
```dataview
LIST
FROM "Literature/Notes"
WHERE contains(file.tags, "LLMs-as-generators")
```

## LLMs as classifiers
- [[comparing_LLMs_BERT.pdf]] - compare encoder- and decoder-model for identifying fakes
- [[synthesis-llm-fake-detection.pdf]] - an overview of LLM existing approaches to classify fakes
- [[dual-role-of-llms.pdf]] - pipeline that generates and then classifies fakes using LLMs
- ==[[debate-to-detect.pdf]] - Multiagent detection to flag misinformation based on debate 

```dataview
LIST
FROM "Literature/Notes"
WHERE contains(file.tags, "LLMs-as-classifiers")
```
## Fact-cheking 
- [[checkthat-overview.pdf]] - overview of solutions on a challenge that finds different solutions for finding check-worthy claims
- [[from-misinfo-to-insight-MLstrategies.pdf]] - an overview of existing ML 
- [[autorship_attribution_for_text_generationpdf.pdf]] - **writing style alone** can be predictive in misinformation contexts.
```dataview
LIST
FROM "Literature/Notes"
WHERE contains(file.tags, "fact-checking")
```
## Propaganda
- ==[[entity-framing.pdf]] ==- frames entitites as protagonist/antagonist/innocent
- [[propaganda-detection.pdf]] - 
- [[Narrative_Similarity.pdf]] - tests different personas (basic vs. specialized) and uses consensus to see which persona-composition decides best

## NLP
- ==[[text-similarity.pdf]]== - different hierarchy levels for evaluating text similarity
- ==[[A_Survey_of_Text_Similarity_Approaches.pdf]]== - #TODO
## Machine Learning
- [[sentence-bert.pdf]] - creates semantically meaningful sentence embeddings that can be compared using cosine-similarity --> https://sbert.net/
- [ ] Write about language and embedding models, what they do. F.e. write about S-BERT and how it works.
- [ ] Write about dimensionality reduction techniques (such as UMAP and t-SNE) -> not sure if that's entirely needed 
- ==[[detecting_stance_in_tweets.pdf]]== - detects stance in tweets
- ==[[GTE-embedder.pdf]]== - general purpose text embedding model 
-   [[SheepDog.pdf]] - model that verifies fakes based on content and not style (useful for catching machine generated fakes)
- [[Its_All_in_the_Embedding_Fake_News_Detection_Usin.pdf]] - fake news detection using sentence embedding models
- ==[[EACL_2026___Confirmation_Bias.pdf]]== - 
- ==[[2024.naacl-demo.8.pdf]]== - Existing biases in instruction-tuned LLMs
- ==[[prompting_survey.pdf]]== - overview over all prompting techniques

```dataview
LIST
FROM "Literature/Notes"
WHERE contains(file.tags, "machine-learning")
```

## Evaluation
- [[bertscore.pdf]] - scoring technique for generated text using contextual embeddings
# Literature Map - what are the takeaways for my work
## Fake News
**Source: [[from-misinfo-to-insight-MLstrategies.pdf]]:**
- Platforms that rely on engagement-driven revenue models contribute to the spread of misleading narratives, making it imperative to integrate detection methodologies that consider not just the textual properties of fake news but also its dissemination patterns.
**Source: [[synthesis-llm-fake-detection.pdf]]**
- Unlike traditional media that has editorial oversight, social media relies on algorithms and user engagement, amplifying sensational or misleading content. 
- fake news is specifically designed to mislead readers by sensationalist headlines and emotionally charged language to gain attention [ 2 ] [ 5]. It spreads very fast through social media since the algorithms prefer engaging content 
**Source: [[Fake News Detection on Social Media-A Data Mining Perspective]]**
- echo chamber effect leads to segmented, homogeneous communities with very limited information ecosystem, which strengthens polarization
 **Source: [[Fake News Net]]:**  a study has shown that the clickbait’s headlines usually can serve as a good indicator for recognizing fake news articles (Chen, Conroy, and Rubin 2015; Shu et al.)
### Datasets

### LLMs as generators

### Fact-checking
