2023 paper
- focused on transcribing written music into a digital format, drawing from disciplines like computer vision, document analysis, and music theory.
- The significance of OMR lies in its contribution to digital humanities, enabling the preservation and accessibility of music as part of cultural heritage.
- The field has benefited significantly from advances in deep learning, but challenges remain, such as reconstructing complex notations, handling multiple voices, and addressing artifacts like lyrics.

#### OMR methods are categorized into two paradigms:

#### **2.1 Pipeline-Based OMR**

- This approach involves sequential stages:
    1. **Preprocessing**: Operations like skew correction, binarization, and staff line removal.
    2. **Symbol Identification**: Detecting and classifying notes, rests, and other symbols.
    3. **Notation Assembly**: Combining detected symbols into larger structures (e.g., measures).
    4. **Encoding**: Translating the final representation into formats like MusicXML or MIDI.
- Each stage relies on specific algorithms and models, but the multi-step process can propagate errors.

#### **2.2 Holistic OMR**

- Holistic methods aim for end-to-end transcription, processing entire sections or pages of music at once.
- Advantages include greater robustness to variations in layout and notation.
- Challenges involve handling overlapping staves, polyphonic music, and complex layouts.

### 3. state of the art
#### **3.1 Pipeline-Based OMR**

- **Symbol Detection**: Deep learning methods like semantic segmentation and object detection have improved symbol classification.
- **Notation Assembly**: Researchers use Graph Neural Networks (GNNs) to model relationships between symbols.
- **Challenges**: The encoding stage is underexplored, and datasets for training and evaluation are limited.

#### **3.2 Holistic OMR**

- Advances in staff detection and staff-level end-to-end transcription are notable.
- Techniques like image-to-sequence models and Connectionist Temporal Classification (CTC) have shown promise.
- Efforts to extend holistic methods to full-page transcription remain limited to monophonic music.

### **4. Current Challenges**

The OMR in this paper includes handwritten scores transcription, which complicates the task. Our project for now should only be concerned with printed scores.

#### **4.1 Pipeline-Based OMR**

- **Symbol Detection**: Variability in musical symbols and formats complicates detection.
- **Notation Assembly and Encoding**: Limited research and datasets hinder development in these areas.

#### **4.2 Holistic OMR**

- **Complex Music Systems**: Current methods struggle with polyphonic music and multi-staff scores.
- **Integration with Language Models**: Limited exploration of using language models to predict musical context.
- **Alignment of Notation and Lyrics**: Essential for vocal music but remains an open problem.
- **Dataset Limitations**: Scarcity of labeled datasets, particularly for handwritten music, restricts progress.

---

### **5. Future Directions**

> [!PDF|red] [[OMR_Advances_Challenges_diresctions_2023_compressed.pdf#page=7&selection=14,0,22,11&color=red|OMR_Advances_Challenges_diresctions_2023_compressed, p.100]]
> > One promising direction is to merge the two branches of research in OMR, namely the pipeline-based and holistic approaches, and move towards end-toend music-notation graph retrieval. This involves developing algorithms that can simultaneously perform staff extraction, music symbol identification, notation assembly, and encoding, using deep learning techniques to model the relationships between different music primitives in a single step. End-to-end approaches have shown promise in other computer vision tasks, and applying similar techniques to OMR can potentially improve recognition accuracy and reduce error propagation
> 
> 

#### **5.1 End-to-End Music Notation Graph Retrieval**

- Proposes merging pipeline-based and holistic methods into a single-step process using deep learning to model relationships between music primitives.

#### **5.2 Synthetic Data Generation and Augmentation**

- Synthetic data can address the scarcity of labeled datasets, enhancing model training and generalization.

#### **5.3 Domain Adaptation Techniques**

- Adapting models to different real-world contexts (e.g., varying notations and scan qualities) to improve robustness.

#### **5.4 Self-Supervised Learning (SSL)**

- Leveraging unlabeled music data for training, enabling general-purpose transcription models across genres and styles.

#### **5.5 Foundational Models for OMR**

- Advocates for creating universal models to standardize and unify OMR methodologies, enhancing comparability and performance.