#machine-learning 
[[Its_All_in_the_Embedding_Fake_News_Detection_Usin.pdf]]

### General
Fakes polarize society and manipulate public opinion -> distorts public perception + social unrest 

#### Methodology:
- Use Word embeddings (Word2Vec, FastText) and Transformers (BERT, RoBERTa, BART) to create DocEmb to embed document + classify using ML approaches
- Pipeline
	- I: News articles -> tokens -> vector model using term weighting schemes (TFIDF) -> word embedding -> document embeddings 
	- II: News articles -> transformer embeddings -> document embeddings
- Preprocessing: remove punctuation and stopword, word lemmatization -> but no preprocessing when using transformer
- Document Embeddings: average all word or transformer embeddings for words appearing in the document 

### Main takeaways for my work
- High accuracy in classification of fakes is in **document encoding**, not classification models
- *President of EU asked for immediate action to be taken against the spread of fake news that undermines democracy and public health* - European Commission. Fighting Disinformation; European Commission: Brussels, Belgium, 2020.
- The difference in performance lies in the embeddings used to vectorize the textual data and how well these perform in encoding contextual and linguistic features.
- Solutions that integrate comments, images and social and network context are called **multimodal learning** -> ex Multimodal Graph CNN
- ==Its BERT + RoBERTa definitions are great==
- Based on this, we can observe that the experiments that use document embeddings that employ transformers perform better than those that employ word embedding on average.

- [ ] #TODO Write about different approaches when working with embeddings (so older approaches used word embeddings and averaging, but newer approaches used transformer embeddings)

- ) The way the word embedding manages to encapsulate the semantic, syntactic, and context features improves the performance of the classification models.

