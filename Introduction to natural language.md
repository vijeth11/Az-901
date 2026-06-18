Here is the corrected and professionally formatted Markdown for your notes on Natural Language Processing (NLP).

---

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

#### TextRank

An unsupervised, graph-based algorithm for extractive summarization and keyword extraction.

1. **Build a Graph:** Sentences/words are nodes; edges represent similarity (e.g., cosine similarity).
2. **Apply Ranking:** Iteratively calculate importance (similar to PageRank).
3. **Select Top Nodes:** Extract the highest-scoring sentences or words.

---

### Semantic Language Models

Modern NLP relies on **embeddings**—encoding tokens as vectors (multi-valued arrays of numbers) in multidimensional space.

* **Vector Geometry:** Semantically similar tokens point in similar directions in vector space.
* **Cosine Similarity:** Used to measure the similarity between two vectors:

$$\text{cosine\_similarity}(A, B) = \frac{A \cdot B}{\|A\| \|B\|}$$



#### Vector Arithmetic and Reasoning

Embeddings enable intuitive algebraic operations:

* **Translation:** $\text{dog} + \text{young} \approx \text{puppy}$
* **Analogy:** $\text{kitten} - \text{puppy} + \text{dog} \approx \text{cat}$

---

### Applications of Semantic Models

* **Text Summarization:** Identifying sentences with vectors most representative of the overall document.
* **Keyword Extraction:** Comparing word embeddings to the document’s aggregate vector.
* **Named Entity Recognition:** Clustering similar entity types together in vector space.
* **Text Classification:** Using document vectors (the mean of word embeddings) as features for machine learning classifiers.
