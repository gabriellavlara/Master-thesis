
## Motivation
- Advancement on Natural Language Generation --> risks associated to it: generate realistic artifacts to trick naive users in fraudulent activities (e.g., machine-generated chatbot conversation in a phishing scam or deepfake-based disinformation campaign)
## Main ideas and conclusions
RQ:
(2) is the given text T written by a human or machine?
A: we find that GPT2 generates texts that are almost indistinguishable from human-written

## Metrics for analyzing linguistics
### Summary statistics metrics
- \# samples
- avg/ sd wordcount
- avg/sd sentence count
### Linguistic features metrics
- Flesch reading ease: how easy it is to understand the text, from 0-100
- Flesch Kincaid grade: US level of education given a certain text
- LIWC- Authentic: author of the text is honest or less evasive
- LIWC-Analytic: formality and logical nature of the text
- LIWC-Article: usage of a/an/the etc
## Main takeaways for my work
- paper 2020: most generators still generate texts significantly different from human-written ones
- GROVER: Grover is another large language model, explicitly trained to generate political news. uses the same model as gpt2--> try and test if Grover can generate tweets?
- Check out their metrics --> reproduce that in my experiments (but at a later phase)
- 