1. Testing my pipeline without vs. with **claim-detection** step.
Basically what this step did was use TextBlob to check the subjectivity of a 
|                          |  | With Claim Detection |
|:--------------------------------|:-----------------------:|:--------------------:|
| Precision@k                     | --                      | --                   |
| Opinion Contamination Rate (%)  | --                      | --                   |
| Mean BERTScore F1               | --                      | --                   |

*Results computed at k=___. Precision@k and Opinion Contamination Rate are averaged across all promptIDs (mean ± std).*

| LLM      | Embeding | k   | Claim detection | Precision@k | Mean BERTScore F1 | Opinion contamination rate |
| -------- | -------- | --- | --------------- | ----------- | ----------------- | -------------------------- |
| DeepSeek | Gemma    |     | 0               |             |                   |                            |
| DeepSeek | M        |     | 1               |             |                   |                            |
