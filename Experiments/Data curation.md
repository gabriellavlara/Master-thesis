1. Collect a series of real news articles of recent events **R**$$
 R=\{{R_{1}, R_{2}, \dots, R_{n}}\}
$$ collected in a time window $$
 [T_{{min}}, T_{max}]
$$ that is *post-training* for all LLMs that will be benchmarked.
Each entry being $$
r_{i} = (id, times tamp, source, title, body, \dots)
$$

2. For each entry in R, collect a set $$H = \{h_{i_{1}}, \dots, h_{ik}\}$$ of human-authored fake news about the same real-world event. 
Posts must follow the criteria (t.b.d):
	- written in English
	- posted on Twitter/Threads 
	- within a defined character-length range
	- ?
They must be pre-filtered for the following aspects:
	- no Emojis
	- removal of external URLs
	- lowercase only

#### **Goal:** build pairs $$(r_{i}, H_{i})
$$ of real news events and their corresponding fake news posts.