[[fighting-firewfire.pdf]]

#LLMs-as-generators 

- This phenomenon is only amplified by social media echo chambers that have demonstrated the ability to shape and polarize public opinion. 
- LLMs can generate misleading content unintentionally (hallucinations) or intentionally by adversarial prompting or jailbreaking (introducing a subtle bias to creating completely fabricated narratives that suit their purpose)
- ****
### Goal: 
- Generate disinformation dataset **FakeSum** using adversarial prompt
- **4 types of disinformation: fabrication, misrepresentation, false attribution and inaccurate quantities**
	- **Misrepresentation:** technically maintaining original story, but introducing bias in the summary. -> biased for and against an entity
- Levels vary from outright false to subtly biased
### Findings
- Both GPT-3.5 and 4 are good at generating correct summaries, but GPT-4 is much better at generating incorrect summaries. + GPT-4 is 15x costlier for the same input and output lenghts
- Prompting GPT-4:
	- Jail-breaking techniques
	- Chain-of-thought prompting
	- Defining summary length and ensuring it doesnt include phrases like "Here is your incorrect summary"
	- Few-shot learning: give some examples of misinformation that is to be produced