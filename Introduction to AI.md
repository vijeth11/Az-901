# Introduction to AI

## Generative AI

1. **Definition**: Branch of AI that creates new content (text, images, video, code).
2. **How it works**: Uses language models trained on large datasets.
   - **Prompts**: Natural language inputs that guide the model’s response.
   - **LLMs vs. SLMs**:
     - **LLMs**: Large, general, powerful, but costly.
     - **SLMs**: Smaller, focused, efficient for specific/local tasks.

## 🤖 Agents

1. **Definition**: Applications built on generative AI that reason, automate tasks, and act contextually.
2. **Key elements**:
   - **Language model** → the agent’s “brain.”
   - **Instructions** → system prompt defining role/behavior.
   - **Tools** → enable interaction:
     - Knowledge tools (search, databases).
     - Action tools (send emails, update calendars, control devices).

## 📘 Common Scenarios

1. Chatbots for Q&A or conversation.
2. AI assistants automating tasks.
3. Content creation (drafts, documents).
4. Translation between languages.
5. Summarization/explanation of complex documents.

## Natural Language Processing (NLP)

1. Enables computers to understand, interpret, and generate human language.
2. Used in tasks like translation, sentiment analysis, summarization, and Q&A.

## Text Analytics in Azure

Azure AI Language provides services for:
- **Sentiment analysis** → positive/negative/neutral tone.
- **Key phrase extraction** → highlights main ideas.
- **Named entity recognition (NER)** → identifies people, places, organizations.
- **Language detection** → determines the language of text.

## Speech

1. Text can be converted to speech and vice versa.
2. Azure Speech service supports transcription, translation, and voice synthesis.
3. **Speech recognition**:
   - Converts spoken audio into text (speech‑to‑text).
   - Enables AI agents to “hear” and interpret human language.
4. **Speech synthesis**:
   - Converts text into spoken audio (text‑to‑speech).
   - Produces increasingly natural, expressive voices.
5. **Challenges in speech AI**:
   - Handling background noise.
   - Detecting interruptions.
   - Generating human‑like intonation and emotion.

## Computer Vision

1. Enables AI systems to interpret and analyze visual data (images, video).
2. Goes beyond simple image recognition → includes detection, classification, segmentation, and analysis.
3. **Types of AI vision**:
   - **Image classification**: Model predicts labels for images.
   - **Object detection**: Model identifies locations of specific objects.
   - **Semantic segmentation**: Identifies individual pixels belonging to objects.
   - **Multi-modal models**: Combine visual features and text descriptions.
4. **Azure Services**:
   - **Azure AI Vision**: Provides OCR, image analysis, and spatial analysis.
   - **Custom Vision**: Train models for specialized classification/detection tasks.
   - **Form Recognizer**: Extract structured data from documents (invoices, receipts, forms).
5. **Information extraction**:
   - Automates insights from unstructured data (documents, images, audio, video).
   - Example: extracting serial numbers from images of computer components.
6. **How it works**:
   - Based on Optical Character Recognition (OCR).
   - Combined with analytical models for field extraction (e.g., receipts → expense claims).
   - Modern models extend to audio, images, and video.

## Core Principles of Responsible AI

1. **Fairness** → Minimize bias in training data and outputs.
2. **Reliability & Safety** → AI is probabilistic; mitigate risks and ensure safe operation.
3. **Privacy & Security** → Protect training data and prevent sensitive leaks.
4. **Inclusiveness** → Ensure solutions are usable by all.
5. **Transparency** → Explain how AI works and its limitations.
6. **Accountability** → Organizations must govern and take responsibility.
7. **Example Scenarios**:
   - College admissions AI → must avoid demographic bias.
   - Robotics with computer vision → act only when confidence is high.
   - Facial recognition in airports → delete temporary images promptly.
   - Speech‑based agents → provide captions for hearing‑impaired users.
   - Loan approval AI → disclose AI usage and training data features.
