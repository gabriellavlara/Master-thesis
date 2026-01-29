[[MuMin-datasetpdf.pdf]]

## Dataset characteristics
- given a Twitter post to be fact-checked and its social context, predict the veracity of the claim made in the Twitter post.
- metadata: source, reviewer, language, verdict (misinformation = false, misleading, pants on fire; factual = true, correct, mostly true) , date
- Tweets: weets should not be replies14, they had to share either a link or an image15 and they had to have been posted at most three days prior to the claim date and at the latest on the claim date itself; minimum of 5 retweets
	- contains the tweet IDs and user IDs --> collect the tweets using twitter API using mumin package 


mumin package
## Might be useful for my work:
- Online misinformation is multimodal (video, image, text), multilingual(but most existing dataset and research only in english) and multitopical (health, politics, celebrities, etc).
- "event-independent predictors of misinformation" --> LLMs need to mimic that 
- [ ] write this phrase + mention that along with linguistic characteristics, generated posts need to be "engagement baits".
- Experiment with Mumin small 
- **==be able to act on stories shared on social media before they go viral==**
- 