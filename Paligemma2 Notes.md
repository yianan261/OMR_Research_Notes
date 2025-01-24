**PaliGemma 2**, a family of Vision-Language Models (VLMs) that improve upon the earlier PaliGemma model. It combines the SigLIP-So400m vision encoder with Gemma 2 language models of varying sizes (3B, 10B, and 28B parameters) and three resolutions (224px², 448px², 896px²). The models are pre-trained across multiple stages and tasks to achieve state-of-the-art results on a broad range of transfer tasks, such as OCR, table structure recognition, music score recognition, and radiography report generation. Open-weight models are released, enabling broad usability.

### **Key Contributions**

1. **Upgraded VLM Family**:
    
    - Combines **SigLIP-So400m vision encoder** with **Gemma 2 language models**.
    - Trained at three resolutions (224px², 448px², 896px²) and model sizes (3B, 10B, 28B).
2. **Transfer Task Expansion**:
    
    - Includes OCR, molecular structure recognition, optical music score recognition, table structure recognition, and radiography report generation.
3. **Performance Analysis**:
    
    - Studies the impact of resolution, model size, and fine-tuning on downstream task performance.
4. **State-of-the-Art Results**:
    
    - Demonstrates improvements in performance over prior models across multiple domains and benchmarks.

---

### **Model Design and Training**

1. **Architecture**:
    
    - Vision encoder generates visual embeddings mapped into the Gemma 2 input space.
    - Gemma 2 autoregressively predicts text tokens based on combined visual and text inputs.
    - Multistage pretraining ensures broad task adaptability.
2. **Training Stages**:
    
    - **Stage 1**: Joint pretraining of vision encoder and language model on low-resolution (224px²) multimodal data.
    - **Stage 2**: High-resolution training (448px² and 896px²) with increased task diversity.
    - **Stage 3**: Task-specific fine-tuning for targeted applications.
3. **Efficiency**:
    
    - Trained on TPUv5 infrastructure.
    - Demonstrates scaling efficiency with minimal quality loss even in reduced precision modes (e.g., quantized CPU inference).

---

### **Experiments and Results**

#### **Core Tasks**

1. **OCR (Text Detection and Recognition)**:
    
    - Fine-tuned on multiple datasets (e.g., ICDAR’15, Total-Text).
    - Outperforms state-of-the-art Hierarchical Text Spotter (HTS) in precision, recall, and F1 scores.
2. **Table Structure Recognition**:
    
    - Benchmarked on PubTabNet and FinTabNet datasets.
    - Achieves the best performance on Tree Edit Distance Similarity (TEDS) and Grid Table Similarity (GriTS).
3. **Molecular Structure Recognition**:
    
    - Translates molecular drawings into SMILES string representation.
    - Surpasses MolScribe on ChemDraw datasets, demonstrating robustness across styles and perturbations.
4. **Optical Music Score Recognition**:
    
    - Recognizes music scores in **kern format.
    - Error rates (Character Error Rate, Symbol Error Rate, Line Error Rate) are significantly lower than previous models.
5. **Radiography Report Generation**:
    
    - Generates clinical reports from X-ray images.
    - Sets new benchmarks for RadGraph F1 scores on the MIMIC-CXR dataset.
6. **Long Caption Generation**:
    
    - Produces detailed image captions using DOCCI dataset annotations.
    - Outperforms other VLMs like MiniGPT-4 and InstructBLIP in factual alignment and fine-grained description.
7. **Spatial Reasoning**:
    
    - Evaluates spatial relationship understanding using Visual Spatial Reasoning (VSR) benchmarks.
    - Achieves substantial accuracy improvements through fine-tuning.

---

### **Performance Insights**

- **Scaling Factors**:
    
    - Higher resolution benefits tasks requiring fine-grained visual details (e.g., OCR, table recognition).
    - Larger models enhance tasks requiring linguistic or contextual reasoning (e.g., spatial reasoning, long captions).
- **Efficiency**:
    
    - Quantized versions maintain performance while reducing computational cost, enabling deployment on resource-constrained devices.

---

### **Conclusion**

PaliGemma 2 represents a versatile, scalable family of vision-language models with exceptional performance across diverse domains. It sets new benchmarks in multiple tasks, extends the applicability of VLMs to novel areas like music score and molecular structure recognition, and demonstrates efficient scaling with quantization for on-device use.

This comprehensive release offers a strong foundation for advancing VLM-based research and applications in both academic and practical contexts.

## Contributions to OMR
### **1. General Architecture**

PaliGemma 2 uses a Transformer-based **image-to-sequence** framework, which integrates a **vision encoder** and a **language model decoder** to process sheet music images and transcribe them into a structured digital music format.

#### **Components:**

1. **Vision Encoder**:
    
    - A pre-trained **SigLIP-So400m encoder** processes sheet music images to extract rich visual features.
    - Features are spatially aware, capturing details such as note shapes, staff lines, and other musical symbols.
2. **Language Model Decoder**:
    
    - Based on the **Gemma 2 language model**, which autoregressively predicts music tokens.
    - Converts the visual features into sequences representing musical notation (e.g., pitch, rhythm, duration).
3. **Output Representation**:
    
    - Music is transcribed into structured formats such as **kern** or other symbolic representations, suitable for playback or editing.

---

### **2. Workflow for OMR in PaliGemma 2**

#### **1: Preprocessing**

- Input: A scanned or digital image of sheet music.
- Preprocessing may include resizing the image to match the resolution required by the vision encoder (224px², 448px², or 896px²).

#### ** 2: Vision Feature Extraction**

- The SigLIP-So400m encoder generates embeddings that represent the visual elements of the sheet music.
- These embeddings capture spatial and contextual relationships, such as the positioning of notes on staves.

#### ** 3: Sequence Decoding**

- The Gemma 2 decoder uses these embeddings as input to predict the sequence of tokens representing the music.
- Tokens include both the content (e.g., notes, rests) and the relationships (e.g., timing, pitch, dynamics) between elements.

#### **4: Postprocessing**

- The predicted sequence is converted into a standard music encoding format, such as **MusicXML** or **kern**, for downstream use.
- The model can handle polyphonic (multi-voice) and complex notations, thanks to its large-scale training and Transformer-based architecture.

---

### **3. Training**

#### **Data**

- PaliGemma 2 uses multimodal datasets that include sheet music images paired with corresponding musical transcriptions.
- Training includes various tasks to ensure the model generalizes to diverse sheet music formats and styles (e.g., handwritten, printed, degraded images).

#### **Multistage Training**:

- **Stage 1**: Pretraining on large-scale multimodal data at lower resolutions (224px²).
- **Stage 2**: Fine-tuning at higher resolutions (448px² or 896px²) with task-specific data to capture fine-grained details.
- **Stage 3**: Fine-tuning for specific applications like OMR.

---

### **4. Key Features for OMR**

1. **Resolution Scaling**:
    
    - High-resolution inputs (up to 896px²) allow the model to process fine details such as small symbols or degraded notations.
2. **Multitask Versatility**:
    
    - The same architecture supports multiple music-related tasks (e.g., optical music score recognition, music transcription, and alignment).
3. **Transfer Learning**:
    
    - Pretrained on a wide variety of visual-text data, the model can adapt to new domains with minimal additional training.
4. **Efficient Decoding**:
    
    - The autoregressive decoder ensures accurate transcription by considering context across the entire sequence of musical symbols.

---

### **5. Results and Impact**

#### **Performance**:

- Achieves state-of-the-art results in OMR benchmarks, reducing error rates compared to previous models.
- Can handle both simple monophonic music and complex polyphonic scores with multiple staves.

#### **Practical Applications**:

- Digitization of sheet music for editing, playback, and analysis.
- Archiving historical sheet music collections.
- Music education tools for teaching notation and performance.