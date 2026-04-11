[[entity-framing.pdf]]
# Entity framing paper

## Background: how news narratives manipulate our emotions by casting entities(people/countries/etc)

- before: labeled framing as "good" or "evil". However, this one sees how entities are framed as "protagonist"/"antagonist"/"innocent" as main-categories.
- calling a group "freedom fighters" vs. "terrorist" manipulates the reader to see the group as protagonist or antagonist. Same story, but completely different perspective. How to objectively classify that without biased judgement of the truth of the event.

## Implementation:

- how is the author of this article making you feel when you read this fact --> narrative role of entities in the document!
- built a dataset of multilingual articles of articles of climate change and RussiaxUkraine war.
- used XMLR to teach multilingual language models and zero-shot LLMs to classify

## Findings:

- "innocent" category: most labeled as "victims" -> implies the existence of a perpretator, induces more outrage. Could be "forgotten", but this is more passive and is not as broadly used.
- "protagonist": peacemaker, guardian.
- role transition: entitites change roles within a single article. An entity starts as a victim -> goes to underdog -> finishes as antagonist.
- 1 single article takes 20min for a HUMAN-expert to decode and identfy the bias. BIG ISSUE, since information grows very fast and is available 24/7!! Does not scale well, so there is the need to have automated solutions to help with categorizing this.
- giving an entire document is tough for an LLM to capture the narrative framing. it is wiser to input sections / paragraphs.
- power of multilingual training: model uses cross-lingual transfers
- prompt engineering: **single step vs. multi step prompting** 
	- multi step: 1. predict the high level category (prot/ant/innocent); 2. predict the low level role (fine grained category)
	- single step (proved superior): figure out the main and fine grained role at once.

## Questions:

- how is propaganda and entity framing related to disinformation? is all propaganda false? is all propaganda potentially harmful?
- emotional claims is not necessarily disinformation, right?