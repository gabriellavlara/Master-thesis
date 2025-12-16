1. Collect a series of real news articles of recent events **R**$$
 R=\{{R_{1}, R_{2}, \dots, R_{n}}\}
$$ collected in a time window $$
 [T_{{min}}, T_{max}]
$$ that is *post-training* for all LLMs that will be benchmarked.
Each entry being $$
r_{i} = (id, times tamp, source, title, body, \dots)
$$

2. For each entry in R, collect a set $$H = \{h_{i_{1}}, \dots, h_{ik}\}$$ of human-authored fake news about the same real-world event. 

 **Define a proxy for the ground truth**, since a human agent won´t annotate the true *(real-news, fake-claim)* pair. The proxy serves as an approximation / closest match to the real news that the person based the fake claim on. [[Questions & Meeting reports]]

Posts must follow the criteria (t.b.d):
	- written in English
	- posted on Twitter/Threads 
	- within a defined character-length range
	- be distorted, and not fabricated fakes. -> 
They must be pre-filtered for the following aspects:
	- no Emojis
	- removal of external URLs
	- lowercase only
	
- [x] #TODO: find existing dataset that contains pairs with (fake_claims, proxies) ✅ 2025-11-18

### Candidate datasets
- PHEME
- Twitter15 and Twitter16
- FakeNewsNet
#### **Goal:** build pairs 
$$(r_{i}, H_{i})
$$
of real news events and their corresponding fake news posts.