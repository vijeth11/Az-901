##### **Introduction to generative AI and agents:-**





###### **Generative AI definition:-**



1. AI that creates new content (text, images, audio, video, code).



2\. Different from traditional AI, which mainly classifies or predicts.



###### **Language models**



1. Trained on large datasets to understand and generate human‑like responses.



2\. Prompts are the inputs that guide the model’s output.



###### **LLMs vs. SLMs**



1. Large Language Models (LLMs) → broad, powerful, but resource‑intensive.



2\. Small Language Models (SLMs) → lighter, efficient, tailored for specific tasks.





###### **Working of LLM:-**



The core fundamental of LLM are trained to complete the prompts by predicting next word based on semantic and linguistic relationship between the previous words in the prompt.

Below is how it is achieved



**Tokenization:-** 



The first step is to provide the model with a large vocabulary of words and phrases known as tokens.  Tokens include words, but also sub-words (like the "un" in "unbelievable" and "unlikely"), punctuation, and other commonly used sequences of characters. The first step in training a large language model therefore is to break down the training text into its distinct tokens, and assign a unique integer identifier to each one, like this: (Note there will be more tokens sourced from internet for training below is a snippet of it)



I (1)

heard (2)

a (3)

dog (4)

bark (5)

loudly (6)

at (7)

a (3) already assigned

cat (8)



**Transforming tokens with a transformer:-**



To relate these tokens with one another we assign each token a vector (an array of multiple numeric values, like \[1, 23, 45]). 
Along with this vector of randomly assigned values before being fed through the transformer to create embedding vectors. The token vectors are fed into the transformer along with a positional encoding that indicates where the token appears in the sequence of training text for example


|Token|Token Id|Position|Vector|
|-|-|-|-|
|I |1|1|\[3, 7, 10]|
|heard|2|2|\[2, 15, 1]|
|a|3|3|\[9, 11, 1]|
|dog|4|4|\[2, 7, 11]|
|bark|5|5|\[9, 12, 0]|
|loudly|6|6|\[3, 8, 13]|
|at|7|7|\[5, 7, 10]|
|a|3|8|\[9, 11, 1]<br />|
|cat|8|9|\[8, -6, 9 ]|



Each vector has multiple numeric elements or dimensions, and we can use these to encode linguistic and semantic attributes of the token to help provide a great deal of information about what the token means and how it relates to other tokens.



We need to transform the initial vector representations of the tokens into new vectors with linguistic and semantic characteristics embedded in them, based on the contexts in which they appear in the training data. Because the new vectors have semantic values embedded in them, we call them embeddings.



To accomplish this task, we use a transformer model. This kind of model consists of two "blocks":



1. Encoder:- It creates the embeddings by applying a technique called attention. The attention layer examines each token in turn, and determines how it's influenced by the tokens around it and assign weights that can be used to calculate the new vector element values. The results of the attention layer are fed into a fully connected neural network to find the best vector representation of the embedding.

2\. Decoder:- This layer that uses the embeddings calculated by the encoder to determine the next most probable token in a sequence started by a prompt. The decoder also uses attention and a feed-forward neural network to make its predictions.

Attention and embedding:-



To determine the vector representations of tokens that include embedded contextual information, the transformer uses attention layers. An attention layer considers each token in turn, within the context of the sequence of tokens in which it appears. The tokens around the current one are weighted to reflect their influence and the weights are used to calculate the element values for the current token's embedding vector. For example, when considering the token "bark" in the context of "I heard a dog bark", the tokens for "heard" and "dog" will be assigned more weight than "I" or "a".



Predicting completions from prompts:-



The decoder model is trained, using data for which we already have the full sequence, by applying a technique called masked attention; in which the tokens after the current token are ignored. 

When predicting a new completion, for which the next tokens are unknown, the attention layers calculate possible vectors for the next token and the feed-forward network is used to help determine the most probable candidate. The predicted value is then added to the sequence, and the whole process repeats to predict the next token; and so on, until the decoder predicts that the sequence has ended.



For example, given the sequence "When my dog was a ...", the model will evaluate the tokens in the sequence so far, use attention to assign weights, and predict that the next most probable token is "puppy" rather than, say, "cat" or "skateboard".





###### **Prompting:-**



A prompt is simply the input or Instructions you give to a generative AI model. The quality of the prompt directly affects the quality of the output.



**Types of Prompt:-**



1. System prompts that set the behavior and tone of the model, and any constraints it should adhere to. For example, "You're a helpful assistant that responds in a cheerful, friendly manner.". System prompts determine constraints and styles for the model's responses.
2. User prompts that elicit a response to a specific question or instruction. For example, "Summarize the key considerations for adopting generative AI described in GenAI\_Considerations.docx for a corporate executive. Format the summary as no more than six bullet points with a professional tone.".



Conversation history:- To keep a conversation consistent and relevant, generative AI apps often keep track of the conversation history; and include summarized versions of it in subsequent prompts. This ensures there’s an ongoing context for the conversation that the model can build on.



Retrieval augmented generation (RAG):- To add even more context, generative AI applications can use a technique called retrieval augmented generation (RAG). This approach involves retrieving information, like documents or emails, and using it to augment the prompt with relevant data. The response generated by the model is then grounded in the information that was provided.



**Prompt engineering:-**



1. Crafting prompts carefully to guide the model toward useful, accurate, and relevant responses.



2\. Includes specifying context, role, format, and constraints.



**Types of prompts:-**



1. Zero‑shot → no examples, just the task.



2\. Few‑shot → provide a few examples to guide the model.



3\. Instructional → explicitly tell the model what role to take or how to respond.



###### **AI Agents:-**



Applications built on generative AI that can reason, act, and interact with context. They combine language models, instructions, and tools to perform tasks.



**Agent Components:-**



1. Language model → the “brain” that interprets prompts and generates responses.



2\. Instructions (system prompt) → define the agent’s role, behavior, and boundaries.



3\. Tools → extend capabilities:



&#x09;a. Knowledge tools (search, databases).



&#x09;b. Action tools (send emails, update calendars, control devices).

