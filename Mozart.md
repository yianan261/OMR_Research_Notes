[Github](https://github.com/aashrafh/Mozart?tab=readme-ov-file#methodology)
The aim of this project is to develop a sheet music reader. This is called Optical Music Recognition (OMR). Its objective is to convert sheet music to a machine-readable version. We take a simplified version where we convert an image of sheet music to a textual representation that can be further processed to produce midi files or audio files like wav or mp3.

## Techniques
### 1. Noise Filtering and Binarization

### 2. Segmentation
[  
![Segment 1](https://github.com/aashrafh/Mozart/raw/main/output/imgs/02/02_seg_0.png)](https://github.com/aashrafh/Mozart/blob/main)  
  
[![Segment 2](https://github.com/aashrafh/Mozart/raw/main/output/imgs/02/02_seg_1.png)](https://github.com/aashrafh/Mozart/blob/main/output/imgs/02/02_seg_1.png)

### 3. Staff Line Detection and Removal
[![No Staff Image 1](https://github.com/aashrafh/Mozart/raw/main/output/imgs/02/02_without_staff_0.png)](https://github.com/aashrafh/Mozart/blob/main)  
  
[![No Staff Image 2](https://github.com/aashrafh/Mozart/raw/main/output/imgs/02/02_without_staff_1.png)](https://github.com/aashrafh/Mozart/blob/main/output/imgs/02/02_without_staff_1.png)
### 4. Construct The New Staff Lines
[![New Staff Image 1](https://github.com/aashrafh/Mozart/raw/main/output/imgs/02/02_with_new_staff_0.png)](https://github.com/aashrafh/Mozart/blob/main)  
  
[![New Staff Image 2](https://github.com/aashrafh/Mozart/raw/main/output/imgs/02/02_with_new_staff_1.png)](https://github.com/aashrafh/Mozart/blob/main/output/imgs/02/02_with_new_staff_1.png)
### 5. Symbol Detection and Recognition
[![Result 1](https://github.com/aashrafh/Mozart/raw/main/output/imgs/02/02_detected_0.png)](https://github.com/aashrafh/Mozart/blob/main)  
  
[![Result 2](https://github.com/aashrafh/Mozart/raw/main/output/imgs/02/02_detected_1.png)](https://github.com/aashrafh/Mozart/blob/main/output/imgs/02/02_detected_1.png)
## Parameters for NN Classifier
```Python
 classifiers = {
        'SVM': svm.LinearSVC(random_state=random_seed),
        'KNN': KNeighborsClassifier(n_neighbors=7),
        'NN': MLPClassifier(activation='relu', hidden_layer_sizes=(200,),
                            max_iter=10000, alpha=1e-4,
                            solver='adam', verbose=20,
                            tol=1e-8, random_state=1,
                            learning_rate_init=.0001,
                            learning_rate='adaptive')
    }
```