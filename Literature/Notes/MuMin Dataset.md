[[MuMin-datasetpdf.pdf]]

## Dataset characteristics
- given a Twitter post to be fact-checked and its social context, predict the veracity of the claim made in the Twitter post.
- metadata: source, reviewer, language, verdict (misinformation = false, misleading, pants on fire; factual = true, correct, mostly true) , date
- Tweets: weets should not be replies14, they had to share either a link or an image15 and they had to have been posted at most three days

prior to the claim date and at the latest on the claim date itself.
## Might be useful for my work:
- Online misinformation is multimodal (video, image, text), multilingual(but most existing dataset and research only in english) and multitopical (health, politics, celebrities, etc).
- "event-independent predictors of misinformation" --> LLMs need to mimic that 
- Experiment with Mumin small 