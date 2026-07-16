# Introduction to Generative AI and Agents

## Generative AI Overview
* **Definition:** Artificial Intelligence designed to create *new* content (text, images, audio, video, code), as opposed to traditional AI which focuses on classification or prediction.
* **Language Models:** Trained on massive datasets to understand and generate human-like responses.
* **LLMs vs. SLMs:**
    * **Large Language Models (LLMs):** Broad, powerful, but resource-intensive.
    * **Small Language Models (SLMs):** Lighter, efficient, and tailored for specific tasks.

---

## How LLMs Work
LLMs function by predicting the next token in a sequence based on the semantic and linguistic relationships between preceding tokens.

### 1. Tokenization
The model breaks text into a vocabulary of "tokens" (words, sub-words, or punctuation). Each token is assigned a unique integer identifier (ID).

### 2. Transforming Tokens (Embeddings)
To process tokens, the model assigns each a **vector** (an array of numbers).
* **Positional Encoding:** Added to the vector to indicate the token's place in the sequence.
* **Embeddings:** Initial vectors are transformed into "embeddings"—vectors that encode the semantic and linguistic characteristics (like tense, sentiment, or part of speech) of the token based on training context.

| Token | Token ID | Position | Vector |
| :--- | :--- | :--- | :--- |
| I | 1 | 1 | [3, 7, 10] |
| heard | 2 | 2 | [2, 15, 1] |
| dog | 4 | 4 | [2, 7, 11] |
| bark | 5 | 5 | [9, 12, 0] |

### 3. The Transformer Model
The transformer consists of two primary blocks:
* **Encoder:** Creates embeddings by applying **Attention**. It examines each token and determines how surrounding tokens influence it, assigning weights to calculate new vector values.
* **Decoder:** Uses these embeddings to predict the next most probable token in a sequence. It uses **Masked Attention** (ignoring future tokens) during training to learn how to generate completions.

---

## Prompting and Context
The quality of a prompt determines the quality of the output.

### Types of Prompts
1.  **System Prompts:** Define the model's behavior, tone, and constraints (e.g., "You are a cheerful assistant").
2.  **User Prompts:** The specific questions or instructions provided to the model.

### Context Enhancement
* **Conversation History:** Keeping track of past turns to ensure consistent, ongoing context.
* **Retrieval Augmented Generation (RAG):** Dynamically retrieving external data (e.g., documents, databases) and injecting it into the prompt to "ground" the model's response in factual, up-to-date information.

### Prompt Engineering Techniques
1.  **Zero-shot:** Providing the task without any examples.
2.  **Few-shot:** Providing a few examples to guide the model's style and logic.
3.  **Instructional:** Explicitly defining the role and formatting requirements.

---

## AI Agents
AI Agents are applications built on Generative AI that can reason, act, and interact with their environment.

### Core Components
* **Language Model (The Brain):** Interprets prompts and generates logic/responses.
* **Instructions (System Prompt):** Defines the agent's role, behaviors, and boundaries.
* **Tools (Extensions):**
    * **Knowledge Tools:** Search engines, vector databases, or internal documentation.
    * **Action Tools:** APIs to send emails, update calendars, or control external software/hardware.
