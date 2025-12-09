#datasets 
- Concerns in the context of disinformation: LLM capabilities, availability (open source models and improvements), improvements in prompting techiques
- Apart from disinformation, other problematic behaviour includes: biased content, inaccurate texts, texts offensive towards groups of people such as gender/race/religion
Their work:
- narratives on: COVID-19, Russo-Ukrainian War, Health, US Elections, and Regional.
- given a title and an abstract - based on existing fact-checkin websites 
- generate news articles based only on the title of the narrative + title and abstract
- Analyse quality of machine generated narratives -> 
### Main takeaways:

- existing LLMs (including open-source ones) can easily generate news articles with real or hallucinated supporting evidence about all kinds of dangerous disinformation narratives
- **disinformation narrative: fabricated or misleading set of ideas and opinions spread to push a certain agenda, manipulate public opinion**
- **All models besides Falcon tend to agree with the disinformation** **narrative** 
- The larger the model, the better-formed the text is, and the more likely it resembles news article. Tendency to agree with news article.
- **LLMs are steerable**: With further prompt-tuning, the quality of the generated disinformation could probably be increased even more. Abstracts can also insert additional knowledge into the models, e.g., some of the LLMs were still not aware of the ongoing Russo-Ukrainian war, and the generated texts were not plausible for that reason. By incorporating abstracts, they were able to overcome this lack of knowledge.
- **LLMs agree with all narratives**: LLMs might be especially dangerous for emerging and/or local disinformation campaigns.
- **Only LLMs with safety features were Falcon and ChatGPT + two models that tend to disagree with narratives**
### Useful for my thesis:
they have all setups for prompting the LLMs in the appendix :) P

### Relates to my work because:

- ![[disinfo-capabilities.png]]
