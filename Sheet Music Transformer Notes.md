**Sheet Music Transformer (SMT)**, an end-to-end OMR model based on a Transformer-based image-to-sequence framework. Unlike prior models, which primarily focus on monophonic transcription, SMT handles **polyphonic scores** (e.g., pianoform and string quartets) without relying on simplifications or specific adaptations. SMT predicts score transcriptions directly in a standard digital music encoding format and demonstrates superior performance compared to state-of-the-art models.

It directly transcribes an input image of sheet music into a sequence of tokens that represent musical information in a structured digital format.

## Results
![[PaliGemma 2- A Family of Versatile VLMs for Transfer_compressed.webp]]

[[PaliGemma 2- A Family of Versatile VLMs for Transfer_compressed.pdf#page=8&rect=42,511,293,774|PaliGemma 2- A Family of Versatile VLMs for Transfer_compressed, p.8]]

#### **Metrics Used**:

- **Character Error Rate (CER)**: Measures the percentage of characters in the predicted transcription that need to be corrected.
- **Symbol Error Rate (SymER)**: Focuses on the musical symbols, evaluating insertions, deletions, and substitutions needed to match the ground truth.
- **Line Error Rate (LER)**: Evaluates the accuracy of entire lines of transcription.

#### **Performance Highlights**:

1. **Music Score Recognition**:
    
    - Achieves **significant reductions in CER, SymER, and LER** compared to prior models.
    - Handles polyphonic scores effectively, maintaining accuracy for complex multi-staff music notation.
2. **Comparison with Baselines**:
    
    - Outperforms specialized models for OMR, such as earlier pipeline-based and end-to-end models.
    - Demonstrates better generalization on unseen data due to its pretraining on diverse multimodal datasets.
3. **High-Resolution Impact**:
    
    - Higher input resolutions (e.g., 448px² and 896px²) improve the ability to recognize fine-grained details in music scores, further reducing error rates.
    
### **Key Contributions**

1. **Novel Model**:
    - SMT is the first image-to-sequence approach designed specifically for transcribing polyphonic music scores.
    - what this means: -
	    - **End-to-End Architecture**:
		    - The approach avoids the traditional multi-stage pipeline of OMR (e.g., staff line detection, symbol classification, and semantic assembly).
		    - Instead, it processes the entire input image in one step, outputting a sequence of tokens that encode the music.
		- **Transformer-Based Framework**:
		    - SMT uses a **Transformer encoder-decoder architecture** for this task.
		    - The **encoder** extracts visual features from the input image, while the **decoder** predicts the output sequence token by token.
		- **Input Representation**:
		    - Images of music scores are divided into patches and tokenized into sequences.
		    - Positional encodings are added to preserve the spatial relationships of these patches, which is critical for understanding the layout of the music notation.
		- **Output Representation**:
		    - The output sequence is represented in a structured digital music format, such as **Humdrum kern**.
		    - This format encodes musical information like pitch, duration, and notation semantics.
		- **Training with Sequence Prediction**:
		    
		    - The model is trained in an autoregressive manner, where the decoder generates one token at a time conditioned on previously generated tokens.
		    - A loss function, such as **cross-entropy**, is used to compare the predicted sequence with the ground truth.
	    
2. **Improved Feature Extraction**:
    - SMT evaluates multiple configurations, such as CNN, Swin Transformer, and ConvNexT-based backbones.
3. **Dataset Expansion**:
    - Adapts existing datasets and creates additional polyphonic music datasets, enhancing the scope of evaluation.

---

### **Intro**

- Music is often preserved as printed or handwritten documents.
- OMR automates transcription of these documents into digital formats, akin to OCR for text.
- Traditional OMR systems are either pipeline-based or holistic (end-to-end). Recent end-to-end models excel in monophonic transcription but struggle with **polyphonic complexity**.
- The authors propose SMT to overcome limitations in handling complex, multi-voice scores.

---

### **2. Challenges in Polyphonic OMR**

1. **Monophonic Limitations**:
    - Existing models simplify polyphonic scores to monophonic scenarios.
    - Vertical collapsing (grouping image features sequentially) prevents handling of simultaneous notes across multiple staves.
2. **Polyphonic Complexity**:
    - Polyphonic scores require simultaneous interpretation of multiple staves, which increases the complexity of transcription.
3. **Alignment Issues**:
    - Aligning simultaneous musical events in polyphonic scores remains a significant challenge.

---

### **3. Sheet Music Transformer (SMT)**

#### **Architecture**

- SMT consists of two components:
    1. **Encoder**:
        - Extracts feature maps from the input image using CNNs or Transformer-based backbones.
    2. **Decoder**:
        - Uses an autoregressive Transformer to predict sequences symbol by symbol, conditioned on previous predictions.
- A **two-dimensional positional encoding** ensures spatial relationships within the image are preserved.
![[Sheet Music Transformer- End-To-End Optical Music Recognition Beyond Monophonic Transcription-compressed 1.webp]]

[[Sheet Music Transformer- End-To-End Optical Music Recognition Beyond Monophonic Transcription-compressed.pdf#page=5&rect=119,107,513,478|Sheet Music Transformer- End-To-End Optical Music Recognition Beyond Monophonic Transcription-compressed, p.5]]

encoder outputs 2D feature map to serve as context to condition decoder
#### **Output Encoding**

- SMT uses the **Humdrum kern format**, a simple text-based encoding widely used in computational music analysis.

---

### **4. Experimental Setup**

#### **Datasets**

1. **GrandStaff**:
    - A dataset of 53,882 pianoform scores with both clean and distorted (low-quality) images.
2. **Quartets**:
    - Newly introduced dataset featuring string quartets, derived from Humdrum transcriptions and augmented with realistic distortions.

#### **Baseline Models**

- The authors compare SMT with state-of-the-art models like CRNN and CNN-based approaches.

#### **Metrics**

- **Character Error Rate (CER)**, **Symbol Error Rate (SER)**, and **Line Error Rate (LER)** evaluate transcription accuracy.

---

### **5. Results**

1. **Performance**:
    - SMT (specifically the ConvNexT-based variant) outperforms baselines on all datasets, especially for polyphonic scores.
    - ConvNexT achieves improvements of up to **91.8% CER reduction** in the Quartets dataset compared to the best baseline.
2. **Complexity Handling**:
    - SMT excels in managing simultaneous events and polyphonic staves, providing outputs with better alignment and usability.
3. **Error Analysis**:
    - Most errors involve minor pitch misplacements or accidental omissions, indicating high syntactic correctness.

---

### **6. Discussion**

- **Improved Usability**:
    - SMT outputs are compatible with musicological tools like MuseScore and Verovio Humdrum Viewer.
- **Metric Limitations**:
    - Standard text-based evaluation metrics penalize errors that are visually or musically insignificant.
- **Visual Fidelity**:
    - SMT successfully captures the structure and layout of polyphonic scores, making it highly suitable for practical use.

---

### **7. Future Directions**

1. **Evaluation Framework**:
    - Develop new evaluation metrics that better capture musicological accuracy.
2. **Segmentation-Free Methods**:
    - Explore full-page transcription without relying on staff segmentation.
3. **Universal Transcription**:
    - Train SMT for diverse music notations using its language modeling capabilities.

---

### **Conclusion**

SMT represents a significant step forward in OMR, demonstrating robust handling of polyphonic scores without requiring pre-processing or simplifications. Its use of a Transformer-based framework sets a new benchmark for future research in complex music transcription.