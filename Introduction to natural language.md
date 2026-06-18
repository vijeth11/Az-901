## Introduction to Natural Language Processing (NLP)

Natural Language Processing (NLP) enables machines to extract meaning, structure, and insights from unstructured text. Organizations use these techniques to transform customer feedback, support tickets, contracts, and social media posts into actionable intelligence.

### Text Analysis Use Cases

Common applications include:

1. **Language Detection:** Determining the language of a text; often the first step in a workflow.
2. **Key Term Extraction:** Identifying important words and phrases to determine themes.
3. **Entity Detection:** Identifying named entities (e.g., people, places, dates, organizations).
4. **PII Detection:** Identifying and redacting sensitive data like names, addresses, and financial info.
5. **Text Classification:** Categorizing documents (e.g., spam filtering).
6. **Sentiment Analysis:** A form of classification that predicts the tone (e.g., positive, neutral, negative).
7. **Text Summarization:** Reducing text volume while retaining salient points.

---

### Tokenization and Pre-processing

**Tokenization** is the first step: breaking a corpus into "tokens" (words, sub-words, or punctuation). Each token is assigned a numeric ID to enable frequency analysis.

#### Pre-processing Techniques

* **Text Normalization:** Converting text to lowercase and removing punctuation. *Note:* Be cautious, as "Mr. Banks" (a person) and "banks" (financial institutions) have different meanings.
* **Stop Word Removal:** Excluding common, low-semantic value words like "the" or "a."
* **N-gram Extraction:** Grouping sequences of words (e.g., "artificial intelligence" as a bigram) for context.
* **Stemming:** Stripping endings ("-ing", "-ed") to reduce words to a root (e.g., "powering" → "power").
* **Lemmatization:** Reducing words to their dictionary form using linguistic rules (e.g., "running" → "run").
* **POS Tagging:** Labeling tokens with grammatical categories (noun, verb, adjective, etc.).

---

### Statistical Text Analysis

#### Frequency Analysis

The simplest way to ascertain document topics by counting the occurrences of normalized tokens.

#### Term Frequency-Inverse Document Frequency (TF-IDF)

This technique calculates a score based on how often a term appears in a document relative to its frequency across a whole collection (corpus).

1. **Term Frequency (TF):** Count of a word in a document. $tf(t, d)$
2. **Inverse Document Frequency (IDF):** Measures how common a word is across all documents. $idf(t) = \log\left(\frac{N}{df(t)}\right)$
3. **TF-IDF Calculation:** $tfidf(t, d) = tf(t, d) \times \log\left(\frac{N}{df(t)}\right)$

* **High Score:** Appears often in one document, rarely in others.
* **Low Score:** Common across many documents.

#### Bag-of-Words

A feature extraction technique that represents text as a vector of word frequencies, ignoring grammar and order. This is commonly used as input for probabilistic classifiers like **Naive Bayes**.
For example, you might use this technique to train a machine learning model that performs email spam filtering. The words "miracle cure", "lose weight fast", and `"anti-aging`` may appear more frequently in spam emails about dubious health products than your regular emails, and a trained model might flag messages containing these words as potential spam.

#### TextRank

An unsupervised, graph-based algorithm for extractive summarization and keyword extraction.

1. **Build a Graph:** Sentences/words are nodes; edges represent similarity (e.g., cosine similarity).
2. **Apply Ranking:** Iteratively calculate importance (similar to PageRank).
3. **Select Top Nodes:** Extract the highest-scoring sentences or words.

For example, consider the following document about cloud computing:

Cloud computing provides on-demand access to computing resources. Computing resources include servers, storage, and networking. Azure is Microsoft's cloud computing platform. Organizations use cloud platforms to reduce infrastructure costs. Cloud computing enables scalability and flexibility.

To generate a summary of this document, the TextRank process begins by splitting this document into sentences:

- Cloud computing provides on-demand access to computing resources.
- Computing resources include servers, storage, and networking.
- Azure is Microsoft's cloud computing platform.
- Organizations use cloud platforms to reduce infrastructure costs.
- Cloud computing enables scalability and flexibility.

Next, edges are created between sentences with weights based on similarity (word overlap). For this example, the edge weights might be:

- Sentence 1 <-> Sentence 2: 0.5 (shares "computing resources")
- Sentence 1 <-> Sentence 3: 0.6 (shares "cloud computing")
- Sentence 1 <-> Sentence 4: 0.2 (shares "cloud")
- Sentence 1 <-> Sentence 5: 0.7 (shares "cloud computing")
- Sentence 2 <-> Sentence 3: 0.2 (limited overlap)
- Sentence 2 <-> Sentence 4: 0.1 (limited overlap)
- Sentence 2 <-> Sentence 5: 0.1 (shares "computing")
- Sentence 3 <-> Sentence 4: 0.5 (shares "cloud platforms")
- Sentence 3 <-> Sentence 5: 0.4 (shares "cloud computing")
- Sentence 4 <-> Sentence 5: 0.3 (limited overlap)

After calculating TextRank scores iteratively using these weights, sentences 1, 3, and 5 might receive the highest scores because they connect well to other sentences through shared terminology and concepts. These sentences would be selected to form a concise summary: "Cloud computing provides on-demand access to computing resources. Azure is Microsoft's cloud computing platform. Cloud computing enables scalability and flexibility."

---

### Semantic Language Models

Modern NLP relies on **embeddings**—encoding tokens as vectors (multi-valued arrays of numbers) in multidimensional space.

* **Vector Geometry:** Semantically similar tokens point in similar directions in vector space.
* **Cosine Similarity:** Used to measure the similarity between two vectors:

$$\text{cosine similarity}(A, B) = \frac{A \cdot B}{\|A\| \|B\|}$$

Calculating similarities between the three words:

dog [0.8, 0.6, 0.1] and cat [0.7, 0.5, 0.2]:

- Dot product: (0.8 × 0.7) + (0.6 × 0.5) + (0.1 × 0.2) = 0.56 + 0.30 + 0.02 = 0.88
- Magnitude of dog: √(0.8² + 0.6² + 0.1²) = √(0.64 + 0.36 + 0.01) = √1.01 ≈ 1.005
- Magnitude of cat: √(0.7² + 0.5² + 0.2²) = √(0.49 + 0.25 + 0.04) = √0.78 ≈ 0.883
- Cosine similarity: 0.88 / (1.005 × 0.883) ≈ 0.992 (high similarity)

dog [0.8, 0.6, 0.1] and tree [0.2, 0.1, 0.9]:

- Dot product: (0.8 × 0.2) + (0.6 × 0.1) + (0.1 × 0.9) = 0.16 + 0.06 + 0.09 = 0.31
- Magnitude of tree: √(0.2² + 0.1² + 0.9²) = √(0.04 + 0.01 + 0.81) = √0.86 ≈ 0.927
- Cosine similarity: 0.31 / (1.005 × 0.927) ≈ 0.333 (low similarity)

cat [0.7, 0.5, 0.2] and tree [0.2, 0.1, 0.9]:

- Dot product: (0.7 × 0.2) + (0.5 × 0.1) + (0.2 × 0.9) = 0.14 + 0.05 + 0.18 = 0.37
- Cosine similarity: 0.37 / (0.883 × 0.927) ≈ 0.452 (low similarity)

The results show that "dog" and "cat" are highly similar (0.992), while "tree" has lower similarity to both "dog" (0.333) and "cat" (0.452). Therefore, tree is clearly the odd one out.

#### Vector Arithmetic and Reasoning

You can add or subtract vectors to produce new vector-based results; which can then be used to find tokens with matching vectors. This technique enables intuitive arithmetic-based logic to determine appropriate terms based on linguistic relationships.

Embeddings enable intuitive algebraic operations:

* **Translation:** $\text{dog} + \text{young} \approx \text{puppy}$
  - For example, using the vectors from earlier:

    - dog + young = [0.8, 0.6, 0.1] + [0.1, 0.1, 0.3] = [0.9, 0.7, 0.4] = puppy
    - cat + young = [0.7, 0.5, 0.2] + [0.1, 0.1, 0.3] = [0.8, 0.6, 0.5] = kitten

* **Analogy:** $\text{kitten} - \text{puppy} + \text{dog} \approx \text{cat}$
  - Vector arithmetic can also answer analogy questions like "puppy is to dog as kitten is to ?"

    - To solve this, calculate: kitten - puppy + dog

      [0.8, 0.6, 0.5] - [0.9, 0.7, 0.4] + [0.8, 0.6, 0.1]
      = [-0.1, -0.1, 0.1] + [0.8, 0.6, 0.1]
      = [0.7, 0.5, 0.2]
      = cat

---

### Applications of Semantic Models

* **Text Summarization:** Identifying sentences with vectors most representative of the overall document.
* **Keyword Extraction:** Comparing word embeddings to the document’s aggregate vector.
* **Named Entity Recognition:** Clustering similar entity types together in vector space.
* **Text Classification:** Using document vectors (the mean of word embeddings) as features for machine learning classifiers.
