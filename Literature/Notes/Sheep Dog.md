 #machine-learning
[[SheepDog.pdf]]

Until now, automated fact checking focused on **style related features: the use of f.e. sensationalist tone VS balanced tone**. Sheepdog has **content-focused veracity attributions**

New problem with LLMs: to evade automatic detection, LLMs can generate fakes but write with the style of a newspaper (so with more serious tone etc) by prompting f.e. "write in the style of the NY Times".

SheepDog model captures style agnostic veracity signals from the news content:
- Built upon a pretrained language model (LM) backbone
- leveraging the strong zero-shot reasoning and generative capabilities of LLMs

LLMs can act as high-quality disinfo generators + it's harder to detect than human written ones

Research question: To what extent can text-based fake news detectors withstand LLM-empowered style attacks?
### Main takeaways for my work:
- Characteristics of fakes and real news are different: fakes often have sensationalism, lack credible sources, exhibit partisan biases
- There is a **style-related vulnerability** in text-based detector
- It is basically an encoder model that uses LLM-generated fakes to enhance the training data (produce more stylistically diverse fakes)


![[sheepdog_example.png]]