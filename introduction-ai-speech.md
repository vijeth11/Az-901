# 📘 Introduction — AI Speech

## 1. Speech Recognition (Speech‑to‑Text)

- Converts spoken language into text.
- Enables transcription, voice commands, and accessibility features.

## 2. Speech Synthesis (Text‑to‑Speech)

- Converts text into spoken audio.
- Used in assistants, accessibility tools, and customer service bots.

---

# ⚡ Key Considerations Before Implementing Speech

Before adding speech capabilities to your application, evaluate these factors:

1. **Audio quality requirements** — Background noise, microphone quality, and network bandwidth affect recognition accuracy.
2. **Language and dialect support** — Verify target languages and regional variations are supported.
3. **Privacy and compliance** — Understand how audio data is processed, stored, and protected.
4. **Latency expectations** — Real‑time conversations need low latency; batch transcription can tolerate delays.
5. **Accessibility standards** — Ensure compliance with WCAG guidelines.

---

# 🎙️ Speech Recognition

Speech recognition (speech‑to‑text) converts spoken language into written text.

### 🔄 Pipeline Stages

1. **Audio capture** → Microphone converts analog sound to digital (e.g., 16 kHz). Filters remove noise.
2. **Pre‑processing (MFCC extraction)**
   - Divide audio into frames (20–30 ms).
   - Apply Fourier transform → frequency domain.
   - Map to **Mel scale** → human hearing sensitivity.
   - Extract ~13 coefficients per frame.

   Example feature vectors:  
    <code>
   Frame 1: [ -113.2, 45.3, 12.1, -3.4, 7.8, ... ]
   Frame 2: [ -112.8, 44.7, 11.8, -3.1, 7.5, ... ]
   Frame 3: [ -110.5, 43.9, 11.5, -2.9, 7.3, ... ]
   </code>

3. **Acoustic modeling** → Map features to phonemes using deep learning (transformers).

- Attention mechanism (contextual resolution).
- Parallel processing (faster than RNNs).
- Contextualized predictions.

Example: Frame 42 → 80% /æ/, 15% /ɛ/, 5% others.

4. **Language modeling** → Grammar, vocabulary, and domain knowledge.

- Statistical patterns (common phrases).
- Context awareness (predict verbs after “I need to”).
- Domain adaptation (medical/legal terms).

5. **Decoding** → Beam search finds best word sequence.
6. **Post‑processing** → Cleanup (capitalization, punctuation, profanity filtering, confidence scoring).

---

# 🔊 Speech Synthesis

Speech synthesis converts text into spoken audio for natural interaction.

### 🔄 Pipeline Stages

1. **Text normalization**

- Expand abbreviations, numbers, symbols.
- Example:
  ```
  Input: "Dr. Smith ordered 3 items for $25.50 on 12/15/2023."
  Normalized: "Doctor Smith ordered three items for twenty-five dollars and fifty cents on December fifteenth, two thousand twenty-three."
  ```

2. **Linguistic analysis**

- Segment text → words/syllables.
- Look up pronunciations in lexicons.
- Apply G2P rules for unknown words.
- Mark syllable boundaries, stress patterns.

3. **Prosody generation**

- Rhythm, stress, intonation (pitch, duration, intensity, pauses).
- Transformer models predict natural prosody.

4. **Speech synthesis (audio generation)**

- Neural vocoders (WaveNet, WaveGlow, HiFi‑GAN).
- Generate audio waveform from phoneme + prosody sequence.

---

# 🎯 Example — Complete Pipeline in Action

Request: `"Dr. Chen's appointment is at 3:00 PM"`

1. **Text normalization** → `"Doctor Chen's appointment is at three o'clock P M"`
2. **Linguistic analysis** → Here it breaks normalized text to words then get pronounciation from lookup table then use G2P to create phoneme(sounds for each letter/small unit in language like:- `The word "cat" has 3 phonemes: /k/, /æ/, and /t/`) and syllable (sounds for largter units like doctor-> `doc-tor` 2 syllable `/ˈdɑktər ˈtʃɛnz əˈpɔɪntmənt ɪz æt θri əˈklɑk pi ɛm/`)
3. **Prosody generation** → Pitch rises on _appointment_, pause after _is_, emphasis on _three_.
4. **Speech synthesis** → Audio waveform generated with natural rhythm and stress.
