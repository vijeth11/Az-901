##### **Introduction to natural language processing concepts:-**





Natural language processing (NLP) uses text analysis that enables machines to extract meaning, structure, and insights from unstructured text. Organizations use text analysis to transform customer feedback, support tickets, contracts, and social media posts into actionable intelligence.



###### **Text Analysis:-**



common use cases for text analysis include:



1. Language detection: Determining the language (or languages) in which text is written - often as the first step in a multi-step text processing workflow.



2\. Key term extraction: Identifying important words and phrases in text, to help determine the topics and themes it discusses.



3\. Entity detection: Identifying named entities mentioned in text; for example, places, people, dates, and organizations.



4\. Personally identifiable information (PII) detection: Identifying and redacting personal details in text, such as names, addresses, telephone numbers, financial account details, and other sensitive information.



5\. Text classification: Categorizing text documents based on their contents. For example, filtering email as spam or not spam.



6\. Sentiment analysis: A particular form of text classification that predicts the sentiment of text - for example, categorizing social media posts as positive, neutral, or negative.



7\. Text summarization: Reducing the volume of text while retaining its salient points. For example, generating a short one-paragraph summary from a multi-page document.





###### **Tokenization**



First step in text analysis: break text (corpus) into tokens. Tokens can be words, sub‑words, punctuation, or combinations. Each token gets a numeric ID → enables frequency counts and analysis. Helps identify common terms and subjects in text. Forms the foundation for more advanced NLP tasks.



**Pre‑processing Techniques:-**



1. Text normalization → Before generating tokens, you might choose to normalize the text by removing punctuation and changing all words to lower case (simplifies analysis but may lose meaning). example:- "Mr Banks has worked in many banks." Here the analyser should be able to differentiate between person "Mr Banks" and "banks"
2. Stop word removal → exclude common words (e.g., “the”, “a”) that add little semantic value.
3. N‑gram extraction → group sequences of words such as "artificial intelligence" or "natural language processing" (unigram, bigram, trigram) for richer context.
4. Stemming → strip endings (“ing”, “ed”) to reduce words to root form. so that words with the same etymological root, like "powering", "powered", and "powerful", are interpreted as being the same token ("power")
5. Lemmatization → reduce words to dictionary form using linguistic rules (e.g., “running” → “run”).
6. Parts of speech (POS) tagging → label tokens with grammatical categories (noun, verb, adjective, etc.).





###### **Statistical text analysis.**



Now after breaking down texts into tokens we can analyse them to infer the meaning out of the text. Some of the common statistical analysis techniques are.



**Frequency Analysis:-**



Perhaps the most obvious way to ascertain the topics discussed in a document is to simply count the number of times each normalized token appears. The assumption is that terms that are used more frequently in the document can help identify the subjects or themes discussed.



**Term Frequency - Inverse Document Frequency (TF-IDF):-**



It is a technique that calculates scores based on how often a word or term appears in one document compared to its more general frequency across the entire collection of documents. With this we can identify which topic is discussed or relevant in a document compared to collection of documents (corpus).



To calculate TF-IDF for terms in an individual document, you can use the following three-step process:



1. Calculate Term Frequency (TF): This is simply how many times a word appears in a document. For example, if the word "agent" appears 6 times in a document, then tf(agent) = 6.



2\. Calculate Inverse Document Frequency (IDF): This checks how common or rare a word is across all documents. If a word appears in every document, it’s not special. The formula used to calculate IDF is idf(t) = log(N / df(t)) (where N is total number of documents and df(t) is the number of documents that contain the word t)



3\. Combine them to calculate TF-IDF: Multiply TF and IDF to get the score: tfidf(t, d) = tf(t, d) \* log(N / df(t))



A high TF-IDF score indicates that a word appears often in one document but rarely in others. A low score indicates that word is common in many documents. 





**"Bag-of-words" machine learning techniques:-**



Bag-of-words is the name given to a feature extraction technique that represents text tokens as a vector of word frequencies or occurrences, ignoring grammar and word order. This representation becomes the input for machine learning algorithms like Naive Bayes, a probabilistic classifier that applies Bayes’ theorem to predict the probable class of a document based on word frequency.



For example, you might use this technique to train a machine learning model that performs email spam filtering. The words "miracle cure", "lose weight fast", and `"anti-aging`` may appear more frequently in spam emails about dubious health products than your regular emails, and a trained model might flag messages containing these words as potential spam.



It can also be used for sentimental analysis to label if the text is "positive" or "negative"



**TextRank:-**



TextRank is an unsupervised graph‑based algorithm used for extractive text summarization and keyword extraction. Inspired by PageRank (Google’s algorithm for ranking web pages).



working:-



1. Build a graph



&#x09;a. Sentences (or words) are nodes.



&#x09;b. Edges represent similarity (e.g., overlap of words, cosine similarity of embeddings).



2\. Apply ranking



&#x09;a. Each node’s importance is calculated iteratively, similar to how PageRank scores web pages.



&#x09;b. Sentences/words with higher scores are considered more central.



3\. Select top nodes



&#x09;a. For summarization → choose top sentences.



&#x09;b. For keyword extraction → choose top words/phrases.





example:-

Suppose we have three sentences:



“AI helps in language translation.”



“Language translation is a key application of AI.”



“AI is also used for speech recognition.”





Step 1:- Build graph



&#x09;a. Each sentence is a node.



&#x09;b. Edges are weighted by similarity (e.g., number of overlapping words).

&#x09;Overlap counts:



&#x09;	S1 ↔ S2: words in common = {AI, language, translation} → weight = 3



&#x09;	S1 ↔ S3: words in common = {AI} → weight = 1



&#x09;	S2 ↔ S3: words in common = {AI} → weight = 1



&#x09;So the graph looks like:



&#x09;Node1 ↔ Node2 (weight 3)



&#x09;Node1 ↔ Node3 (weight 1)



&#x09;Node2 ↔ Node3 (weight 1)





Step 2:- Apply TextRank Formula



TextRank(Sᵢ) = (1-d) + d \* Σ(wⱼᵢ / Σwⱼₖ) \* TextRank(Sⱼ) (where d is a damping factor, typically 0.85, wⱼᵢ is the weight of the edge from sentence j to sentence i, and the sum iterates over all sentences connected to i).



Initial scores: all nodes = 1.



Iteration 1 (approx):



Node1 = (1-0.85) + 0.85 × \[(3/4 × 1) + (1/2 × 1)] = 0.15 + 0.85 × (0.75 + 0.5) = 1.325



Node2 = 0.15 + 0.85 × \[(3/4 × 1) + (1/2 × 1)] = same as Node1 = 1.325



Node3 = 0.15 + 0.85 × \[(1/2 × 1) + (1/2 × 1)] = 0.15 + 0.85 × 1 = 1.0



After normalization, Node1 and Node2 have higher scores.





Step 3: Select Top Sentences



Highest scores: Node1 and Node2. Summary = Sentences 1 + 2.





###### **Semantic language models (techniques used for linguistic and semantic embedding):-**



As the state of the art for NLP has advanced, the ability to train models that encapsulate the semantic relationship between tokens has led to the emergence of powerful deep learning language models. At the heart of these models is the encoding of language tokens as vectors (multi-valued arrays of numbers) known as embeddings.





**Representing text as vectors:-**



Vectors represent points in multidimensional space, defined by coordinates along multiple axes. Each vector describes a direction and distance from the origin. Semantically similar tokens should result in vectors that have a similar orientation – in other words they point in similar directions.



example:-



Word	Vector

dog	\[0.8, 0.6, 0.1]

puppy	\[0.9, 0.7, 0.4]

cat	\[0.7, 0.5, 0.2]

kitten	\[0.8, 0.6, 0.5]

young	\[0.1, 0.1, 0.3]

ball	\[0.3, 0.9, 0.1]

tree	\[0.2, 0.1, 0.9]





The semantic characteristic encoded in the vectors makes it possible to use vector-based operations that compare words and enable analytical comparisons.



**Finding related terms:-**



**Since the orientation of vectors is determined by their dimension values, words with similar semantic meanings tend to have similar orientations. This means you can use calculations such as the cosine similarity between vectors to make meaningful comparisons.**



**example calculating cosine similarity between dog, cat, tree**



cosine\_similarity(A, B) = (A · B) / (||A|| \* ||B||)



1. dog \[0.8, 0.6, 0.1] and cat \[0.7, 0.5, 0.2]:



&#x09;a. Dot product: (0.8 × 0.7) + (0.6 × 0.5) + (0.1 × 0.2) = 0.56 + 0.30 + 0.02 = 0.88

&#x09;b. Magnitude of dog: √(0.8² + 0.6² + 0.1²) = √(0.64 + 0.36 + 0.01) = √1.01 ≈ 1.005

&#x09;c. Magnitude of cat: √(0.7² + 0.5² + 0.2²) = √(0.49 + 0.25 + 0.04) = √0.78 ≈ 0.883

&#x09;d. Cosine similarity: 0.88 / (1.005 × 0.883) ≈ 0.992 (high similarity)

&#x09;

2\. dog \[0.8, 0.6, 0.1] and tree \[0.2, 0.1, 0.9]:



&#x09;a. Dot product: (0.8 × 0.2) + (0.6 × 0.1) + (0.1 × 0.9) = 0.16 + 0.06 + 0.09 = 0.31

&#x09;b. Magnitude of tree: √(0.2² + 0.1² + 0.9²) = √(0.04 + 0.01 + 0.81) = √0.86 ≈ 0.927

&#x09;c. Cosine similarity: 0.31 / (1.005 × 0.927) ≈ 0.333 (low similarity)



3\. cat \[0.7, 0.5, 0.2] and tree \[0.2, 0.1, 0.9]:



&#x09;a. Dot product: (0.7 × 0.2) + (0.5 × 0.1) + (0.2 × 0.9) = 0.14 + 0.05 + 0.18 = 0.37

&#x09;b. Cosine similarity: 0.37 / (0.883 × 0.927) ≈ 0.452 (low similarity)



**Vector translation through addition and subtraction:-**



we can add or subtract vectors to generate new vector results which can then be used to find tokens with matching vectors. This technique enables intuitive arithmetic-based logic to determine appropriate terms based on linguistic relationships.

For example, using the vectors from earlier:



&#x09;dog + young = \[0.8, 0.6, 0.1] + \[0.1, 0.1, 0.3] = \[0.9, 0.7, 0.4] = puppy

&#x09;cat + young = \[0.7, 0.5, 0.2] + \[0.1, 0.1, 0.3] = \[0.8, 0.6, 0.5] = kitten



These operations work because the vector for "young" encodes the semantic transformation from an adult animal to its young counterpart.

The arithmetic works in reverse as well:



&#x09;puppy - young = \[0.9, 0.7, 0.4] - \[0.1, 0.1, 0.3] = \[0.8, 0.6, 0.1] = dog

&#x09;kitten - young = \[0.8, 0.6, 0.5] - \[0.1, 0.1, 0.3] = \[0.7, 0.5, 0.2] = cat



**Analogical reasoning:-**



Vector arithmetic can also answer analogy questions like "puppy is to dog as kitten is to ?"



To solve this, calculate: kitten - puppy + dog



\[0.8, 0.6, 0.5] - \[0.9, 0.7, 0.4] + \[0.8, 0.6, 0.1]

= \[-0.1, -0.1, 0.1] + \[0.8, 0.6, 0.1]

= \[0.7, 0.5, 0.2]

= cat



These examples demonstrate how vector operations can capture linguistic relationships and enable reasoning about semantic patterns.



###### **Using semantic models for text analysis:-**



Text summarization:- Semantic embeddings enable extractive summarization by identifying sentences with vectors that are most representative of the overall document.



Keyword extraction:- Vector similarity can identify the most important terms in a document by comparing each word's embedding to the document's overall semantic representation. Words whose vectors are most similar to the document vector, or most central when considering all word vectors in the document, are likely to be key terms that represent the main topics.



Named entity recognition:- Semantic models can be fine-tuned to recognize named entities (people, organizations, locations, etc.) by learning vector representations that cluster similar entity types together.



Text classification:- For tasks like sentiment analysis or topic categorization, documents can be represented as aggregate vectors (such as the mean of all word embeddings in the document). These document vectors can then be used as features for machine learning classifiers, or compared directly to class prototype vectors to assign categories.

