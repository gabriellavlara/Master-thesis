#LLMs-as-generators 
# Fighting fire with fire: the dual role of LLMs in crafting and detecting elusive disinformation

## Main idea:
**RQ1: Can LLMs be exploited to efficiently generate disinformation using prompt engineering?**

**RQ2: How proficient are LLMs in detecting
disinformation?**



### Pipeline
1. Paraphrase and perturbation prompt to create synthetic disinfo from real human-written news -> prompting methods for disinfo generation

2. Hallucination mitigation + validation -> makes sure data remains grounded in factual sources

3. Disinformation detection using zero-shot chain-of-thought 

### Disinfo generation
A synthetic fake consists of a generated text based on a prompting strategie that contains **content C, impersonator R and instructor I**. 



### Prompting
- **prefix prompts**: use paraphrasing + perturbation for synthetic generation

Impersonator sets contextual behavior intent and instructions. It´s useful for overriding safety features that comercial LLMs have. 

Different perturbation-based fakes:
- minor: barely identifiable, f.e. by changing numbers
- major: 
- critical: conspicuous changes to real news, easily detectable

Paraphrase-based real news:

- Minor paraphrase: summarizes / rephrases 
- Major prompt: changes structure and wording
- Critical prompt: changes tone and structure  

### Validation
- Natural Language Inference to eliminate instrincic hallucinations (generated output contradicts prompt)
- AlignScore to eliminate extrinsic hallucination (generated output doesnt match prompt)
- Semantic Distance to tackle incoherence
- BERTScore to target unrelated context generation

These steps make sure the generated news aligns logically and factually with the prompt w.r.t input text. 

### Interesting results
To the research questions: 

- LLMs struggle more to
detect human-written disinformation, compared to LLM-generated variants.
- LLMs exhibit superior
zero-shot performance on (long) news articles than (short) social media posts
- LLMs show better zeroshot performance on in-distribution data, except LLaMA-2
- Fine-tuned detectors significantly outperform LLMs and domainspecific detectors but are not consistent on
detecting OOD disinformation. GPT3.5-
Turbo outperforms domain-specific detectors while other LLMs perform comparably

In general:
- generative LLMs’ applicability in real-world settings as emerging zero-shot reasoners in disinformation detection
- Smart, cunningly crafted (subtle) disinformation challenges even the best current detectors.


## Limitations 
- Bypassing safety alignment is not always consistent. F.e. persona based prompting worked for most LLMs, but failed for Falcon (it only worked with Chain-of-Thought prompting)
- Few-shot prompting
- test larger models like GPT4
- adding multimodal inputs


## Useful for my work:
- Prompting techniques they use - > stucture that contains C,R,I
- Persona-based prompting circumvents GPT´s safety alignments -> finding : Impersonator prompt engineering overrides GPT-3.5-turbo’s protections, enabling malicious text generation
despite alignment tuning.
- 38% of data contains hallucinated misalignments between generated text and input prompt -> watch out for that. They deanveloped **PURIFY** as a solution
- **unseen data for out-of-distribution generalization**


