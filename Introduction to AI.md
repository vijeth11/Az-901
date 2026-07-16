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

1. **Fairness** → AI developers need to take care to minimize bias in training data and test AI systems for fairness.
2. **Reliability & Safety** → AI works on probabilities, not certainties.It can make mistakes.Applications must plan for errors and reduce risks.
3. **Privacy & Security** → AI developers have a responsibility to ensure that the training data is kept secure, and that the trained models themselves can't be used to reveal private personal or organizational details.
4. **Inclusiveness** → The potential of AI to improve lives and drive success should be open to everyone. AI developers should strive to ensure that their solutions don't exclude some users.
5. **Transparency** → AI can sometimes seem like "magic", but it's important to make users aware of how the system works and any potential limitations it may have.
6. **Accountability** → Ultimately, the people and organizations that develop and distribute AI solutions are accountable for their actions. It's important for organizations developing AI models and applications to define and apply a framework of governance to help ensure that they apply responsible AI principles to their work.
7. **Responsible AI examples**
   - **Some example of scenarios where responsible AI practices should be applied include :-**
      - An AI-powered college admissions system should be tested to ensure it evaluates all applications fairly, taking into account relevant academic criteria but avoiding unfounded   discrimination based on irrelevant demographic factors.
      - An AI-powered robotic solution that uses computer vision to detect objects should avoid unintentional harm or damage. One way to accomplish this goal is to use probability values to determine "confidence" in object identification before interacting with physical objects, and avoid any action if the confidence level is below a specific threshold.
      - A facial identification system used in an airport or other secure area should delete personal images that are used for temporary access as soon as they're no longer required. Additionally, safeguards should prevent the images being made accessible to operators or users who have no need to view them.
      - An AI agent that offers speech-based interaction should also generate text captions to avoid making the system unusable for users with a hearing impairment.
      - A bank that uses an AI-based loan-approval application should disclose the use of AI, and describe features of the data on which it was trained (without revealing confidential information).

#### **Note:-** Read Azure AI Foundry Document expecially tools section to understand what pre-built tools are given [AI Foundry Doc](https://learn.microsoft.com/en-us/azure/foundry/)
