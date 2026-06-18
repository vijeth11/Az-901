## Introduction to AI Speech

### Core Technologies
1.  **Speech Recognition (Speech-to-Text):** Converts spoken language into text. Enables transcription, voice commands, and accessibility features.
2.  **Speech Synthesis (Text-to-Speech):** Converts text into spoken audio. Used in virtual assistants, accessibility tools, and customer service bots.

### Key Considerations Before Implementation
* **Audio Quality:** Background noise, microphone quality, and bandwidth affect accuracy.
* **Language/Dialect:** Ensure target languages and regional variations are supported.
* **Privacy & Compliance:** Adhere to regulatory requirements for audio processing and storage.
* **Latency:** Real-time conversations require low-latency, while batch transcription allows delays.
* **Accessibility:** Ensure compliance with WCAG guidelines.

---

## Speech Recognition Pipeline
Speech recognition converts audio signals into written text through six stages:

1.  **Audio Capture:** Microphone converts analog sound to digital (typically 16 kHz). Noise filtering removes hums and clicks.
2.  **Pre-processing (Feature Extraction):** Uses MFCCs (Mel-Frequency Cepstral Coefficients) to mimic human hearing.
    * **Framing:** Split signal into 20–30ms windows.
    * **Fourier Transform:** Convert time domain to frequency domain.
    * **Mel Mapping:** Adjust frequencies to match human sensitivity.
    * **Coefficient Extraction:** Summarize spectral shapes into feature vectors.
3.  **Acoustic Modeling:** Maps features to **phonemes** (the smallest units of sound). Transformer models use attention mechanisms and parallel processing to handle context and ambiguity.
4.  **Language Modeling:** Applies grammar and domain knowledge to resolve ambiguity.
5.  **Decoding:** Beam search identifies the most probable word sequence.
6.  **Post-processing:** Cleans raw text (capitalization, punctuation, profanity filtering).

---

## Speech Synthesis Pipeline
Converts written text into natural-sounding speech.

1.  **Text Normalization:** Expands abbreviations, numbers, and symbols into spoken forms.
2.  **Linguistic Analysis:** Maps text to phonemes using lexicons and Grapheme-to-Phoneme (G2P) conversion.
3.  **Prosody Generation:** Determines rhythm, stress, and intonation patterns using transformer neural networks.
4.  **Speech Synthesis (Vocoding):** Deep learning neural vocoders (e.g., HiFi-GAN, WaveNet) generate the final audio waveform.
