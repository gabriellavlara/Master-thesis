[[generate-first-then-sample.pdf]]
#LLMs-as-generators 

- Fake news has high concerns in areas such as public health and politics
	- Can mislead public and cause unrest

- To this date: Early approaches focus on building deep learning models to learn better representations of news articles for detection purposes (Wang et al., 2018a). Subsequent works have leveraged the social context of news and external knowledge (Wu et al., 2024). With the advent of Large Language Models (LLMs), recent studies have increasingly exploited the reasoning capabilities of LLMs (Hu et al., 2024; Xu et al., 2023), as well as their enhancement of news content (Park et al., 2024), social context (Nan et al., 2024), and external knowledge (Tian et al., 2024).
	- Early work: detect fakes using linguistic features
	- NN to capture semantic meaning of news
	- Integrate external knowledge related to the news 
	- With LLMs: make use of its reasoning capabilities to detect fakes; use it ot augment the news 
	- Problem: fakes are often underrepresented in existing datasets
- **Ideal fake news detector**
	- 1. have good performance, even with limited amount of news data
	- 2. Have data distribution awareness 
#### Their contribution:
Generate First and then Sample for Fake News Detection:
- Original and generated fake news are included in training set -> mitigate underrepresentation of fakes in the original dataset
- Reinforcement Learning to learn optimal ration of real-to-fake news during training

The task: binary classification problem, with $$
y_{i} \in \{0, 1\}
$$ being whether the true label of a news item is real or fake, respectively.

**Fake news generation**
- Chain-of-thought prompt:
	- List key points in the original fake news
	- ==Rewrite, expand or disguise== the news while keeping the semantics of it
- Dataset: GossipCop




![[generate-first-then-sample.pdf]]
