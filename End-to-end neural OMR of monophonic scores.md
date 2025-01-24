paper proposes a model that combines Convolutional Neural Networks (CNNs) and Recurrent Neural Networks (RNNs) with a **Connectionist Temporal Classification (CTC)** loss function, enabling training directly from images paired with musical transcripts.

- **Input and Output**:
    - Input: Grayscale staff images.
    - Output: Sequence of music symbols, encoded either semantically or agnostically.
- **Neural Network Design**:
    
    - Uses a **Convolutional Recurrent Neural Network (CRNN)** combining CNN layers (for visual feature extraction) with bidirectional LSTM layers (for sequence modeling).
    - Trains using the **CTC loss function**, which aligns the sequence prediction without requiring explicit positional annotations for symbols.
    - Uses CNN to process input image, RNN responsible for producing sequence of musical symbols that fulfills equation 
    
- **Semantic and Agnostic Representations**:
    
    - **Semantic**: Encodes symbols with musical meaning (e.g., notes, rests).
    - **Agnostic**: Encodes symbols as visual features without musical meaning (e.g., a sharp symbol).
    -  where x_i is the single staff image and y_i is corresponding sequence of music symbols
    - x is a sequence of variable length, given by number of columns. y is sequence of music symbols
![[End-to-End Neural Optical Music Recognition of Monophonic Scores_compressed 1.webp]]

[[End-to-End Neural Optical Music Recognition of Monophonic Scores_compressed.pdf#page=4&rect=147,430,449,559&color=red|End-to-End Neural Optical Music Recognition of Monophonic Scores_compressed, p.4]]
### **Experiments and Results**

1. **Dataset and Training**:
    
    - The **PrIMuS dataset** consists of 87,678 staves, with both agnostic and semantic representations. 
	    > [!PDF|red] [[End-to-End Neural Optical Music Recognition of Monophonic Scores_compressed.pdf#page=5&selection=12,0,13,101&color=red|End-to-End Neural Optical Music Recognition of Monophonic Scores_compressed, p.5]]
> > PrIMuS contains 87 678 real-music incipits (an incipit is a sequence of notes, typically the first ones, used for identifying a melody or musical work), each one represented by five files (see Figure 1)
    - The model was trained using **stochastic gradient descent (SGD) with the Adadelta optimizer.
    
1. **Performance**:
    
    - **Semantic representation** outperformed agnostic representation:
        - Sequence Error Rate: 12.5% (semantic) vs. 17.9% (agnostic).
        - Symbol Error Rate: 0.8% (semantic) vs. 1.0% (agnostic).
    - Errors predominantly involved less frequent symbols like ties and grace notes.
3. **Comparison with Commercial Tools**:
    
    - The model demonstrated competitive performance compared to **Photoscore Ultimate**, with better accuracy and faster prediction times (1 second per score on average).
4. **Localization**:
    
    - While the model successfully predicted symbol sequences, it lacked precise localization due to the design of the CTC loss function.

---

### **Conclusions**

1. The proposed **end-to-end neural OMR system** successfully addresses the limitations of traditional multi-stage pipelines.
2. **Semantic encoding** provides better results due to the model’s ability to leverage musical context.
3. The approach is computationally efficient, making it suitable for interactive applications.