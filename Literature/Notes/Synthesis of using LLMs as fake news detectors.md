#LLMs-as-classifiers 
[[synthesis-llm-fake-detection.pdf]]

General info about fakes:
- multimodal: so needs to analyze visual and textual cues
- sensationalist headlines and emotionally charged language
Early approaches relied on manually extracted features, such as linguistic or psychologic cues --> **limitation: generalization abilities across domains, restricted to detecting less sophisticated patterns of disinfo**

LLM usage for this task: allow large- scale knowledge and reasoning competencies
There are approaches that integrate both (other ML algorithms such as GNN + LLMs) - e.g. MilkFD .
Other approaches such as FND-LLM are good for multimodal processing (so LLM would process text, CNN image)
SheepDog tries to identify fakes based on content and not writing style (very robust for LLM genrated fakes, that try to copy how real news would post)

Limitations of existing approaches: 
- over-reliance on textual features - they mostly disregard multimodal and contextual cues
- Scalability Issues in Real-Time Detection: Most current models lack the processing capability for volume and velocity, information generated within social media undermines scalability, and practical applicability in dynamic environments
- Lack of Transparent Models to Explain Predictions
### Main takeaways for me:
- [x] #TODO: write limitations or what is missing for each approach on fake news detection so far. In the case of older ML approaches, say they didnt generalize well and were less robust ✅ 2025-10-24
- Check out SheepDog paper + PolitiFact dataset
