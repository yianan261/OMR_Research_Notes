## CNN with UNet Models
[[OEMER]]

## Computer Vision System
[[cadenCV]]
## Classifier
SVM  ([[Mozart]])
KNN ([[Mozart]])
NN (MLP) ([[Mozart]])

### VIT
[[VIT based approach]]

### Transformers
[[Transformers]]

### Language Model
[[LLM Based]]

### Seq2seq
[[Seq2seq]]

### GraphNN
[[Graph NN]]

## RNN
[[RNN]]

## Preprocessing

[[Mozart]]: Noise filtering and binarization, segmentation, symbol detection and recognition
[[cadenCV]]: Noise filtering and binarization, 

> [!PDF|red] [[understandingOMR.pdf#page=21&selection=8,0,27,64&color=red|understandingOMR, p.21]]
> > 1) Preprocessing: Standard techniques to ease further steps, e.g., contrast enhancement, binarization, skew-correction or noise removal. Additionally, the layout should be analyzed to allow subsequent steps to focus on actual content and ignore the background. 2) Music Object Detection: Finding and classifying all relevant symbols or glyphs in the image. 3) Notation Assembly: Recovering the music notation semantics from the detected and classified symbols. The output is a symbolic representation of the symbols and their relationships, typically as a graph. 4) Encoding: Encoding the music into any output format unambiguously, e.g., into MIDI for playback or MusicXML/MEI for further editing in a music notation program.


## Datasets

### [[OEMER]]
[CvcMuscima-Distortions](http://pages.cvc.uab.es/cvcmuscima/index_database.html) for training the first model, and [DeepScores-extended](https://zenodo.org/record/4012193) for 2nd model

