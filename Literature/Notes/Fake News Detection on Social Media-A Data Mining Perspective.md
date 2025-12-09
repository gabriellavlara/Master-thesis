[[fakenews-detection-data-mining.pdf]]
#fakenews 

- Challenges in social media fake detection: need to include auxiliary info such as social engagements and knowledge base
- the most popular fake news was even more widely spread on Facebook than the most popular authentic mainstream news during the U.S. 2016 president election
- **Fake news is usually manipulated by propagandists to convey political messages or influence**
- Fakes change the way people respond to real news - it triggers them and makes them confuse (source 6https://www.nytimes.com/2016/11/28/opinion/fake-news-and-the-internet-shell-game.html? r=0)
- Problems with fakes: may cite true evidence to support non-factual claim; usually related to newly emerging, time-critical events which may not have been yet verified by existing knowledge bases 
### Characterization of fakes
- Definition: news that are intentionally and verifiably false and could mislead readers --> **authenticity & intent**
- Factors that make people more prone to believing in fakes: naive realism (only ones perception is the accurate one, all others are irrational/biased/uninformed) + confirmation bias (they prefer info that confirms their preexisting views)
- Problems of social media:
	- social bots that spread fakes or distort news -> around 19 million accounts supported either Trump or Clinton in the week leading to election days (8http://comprop.oii.ox.ac.uk/2016/11/18/resource-for-understanding-political-bots/)
	- trolls: real humans who use social media to disrupt online comunities-> around 1k russian trolls paid to spread fakes on hillary clinton
	- echo chamber: consumers are selectively exposed to certain kinds of news because of the way the news feed appears on their homepage -> f.e. users follow like minded people and thus receive news that promote their vision/narratives --> **segmented, homogeneous communities with very limited information ecosystem**
	- social credibility and frequency heuristic (the more often one hears about an info makes it more credible)
### Detection of fakes
Two phases: feature extraction and model construction
Feature extraction:
- news attributes
	- source
	- headline
	- body text
	- image/video
- fake news often contain **inflammatory language** as clickbait -> sensational headlines and writing styles
- linguistic features:
	- lexical features: total words, character per word, frequency of large words, unique words
	- synthetic features: n-grams, punctuations, parts-of-speech tagging
- visual features:
	- clarity score, coherence score, similarity distribution histogram, diversity score, clustering score, image ration, etc
- social context features:
	- user-based features: characteristics of users who interact with post (see the credibility of individuals who interact w news )
	- post-based: users reactions to the news (supporting, denying, credibility)
	- network-based: stance network (nodes indicating all tweets and their stance on it); cooccurence network (how many other posts relevant to that article are posted)
### News content models
- Knowledge based models: use external sources to fact-check
- Style-based: capture f.e style signals such as extreme behaviour in favor of a political party, clickbait headlines, 
### Model
- Classification problem where TP = when predicted fake is actually annotated as fake; TN = when predicted real news is annotated as true
- Metrics for evaluating performance: precision, recall, f1, accuracy, TPR; TNR; AUC (more statistically consisent and discriminating than accuracy, specially for imbalanced distributions)
- 
