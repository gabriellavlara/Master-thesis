[[Narrative_Similarity.pdf]]

# Main ideas
- multiperspectivity should be incorporated as a modeling component
- Multiagent debate as a strategy for improving LLM reasoning and decision making. 
- Narrative similarity task: given one Anchor story and two candidate stories A and B, decide which candidate is most similar to anchor.
- Personas: practitioner (specialist with more analytical focus) vs. Lay-person (general persona)

# Key takeaways
- Given one query LLM-generated false post and a set of candidate human-authored posts, flag the ones that are most similar to query post. 
- more complicated roles (in persona based prompting) can lead to performance decreases when compared to simpler personas (Kim et al 2025)
- Cross-model majority vote: should i do something that f.e. a post that is flagged by multiple models gets priority? Am not sure...
- Have results averaged over n=10 runs? So f.e. X +- std
- GPT also underperformed the other models - why is that? any assumptions?
- "Several limitations of this thesis should be aknowledged"