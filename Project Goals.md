1/7/2025:
1. Need a working demo
## steps
1.  find open source project first (then we have something to demo, we improve)
2. first try to run on computer, have working project. then on top of that revise, then train model/improve, figure out how to improve
3. identify some projects (find on github)

reach out to authors for source code

create github project

lead most implementation

resources: GPU server → not for LLM

mode of communication (rent GPU)

For our project we're concerned with the **replayability** (extraction of music from score to a form that can be played back by computer, without requiring the output to be human-readable); whereas **Structured Encoding** is about extracting both the music and **how it was encoded** visually, preserving the **human-readable notation** for purposes like printing, editing, or performance.

## Goals
1. Improve upon current OMR systems/algorithms and generate MIDI files or other formats from printed music sheets/scores
2. Generate audio files from the MIDI files to synthesis software to produce audio file
3. Transcribing OMR -> developing pipeline of converting sheet music into machine-readable format. Process includes extraction, interpretation, and encoding musical information from printed symbols on the page and produce digital representation that preserves music's content and structure. Final goal is to generate audio format of that digitized representation. Should combine both combine **agnostic** and **semantic** representations to balance the strengths of each approach.

1. **Agnostic Phase**: Identifies and classifies symbols visually.
2. **Semantic Phase**: Interprets the identified symbols in their musical context.

This hybrid approach ensures accurate transcription while preserving flexibility for different use cases, such as creating a digital score for editing or playback.

2025/01/24:
1. play with the models 
2. proposal for ensemble learning
3. 
## Current Literature
[[Literature and Github]]

## Evaluation
[[Evaluation]]

### Questions
[[Questions]]
The definitions of OMR and some OMR research includes handwritten manuscripts (https://link.springer.com/chapter/10.1007/978-3-031-41498-5_7?fromPaywallRec=false)

Our project scope right now should not include handwritten manuscripts but offline typeset/printable music sheets/scores

## Current pain points
1. Music Object Detection not ideal for densely packed objects (such as polyphonic scores)
> [!PDF|red] [[understandingOMR.pdf#page=24&selection=50,0,56,39&color=red|understandingOMR, p.24]]
> > Music Object Detection: recent work has shown that the music object detection stage can be addressed in one step with deep neural networks. However, the accuracy is still far from optimal, which is especially detrimental to the following stages of the pipeline that are based on these results. In order to improve the detection performance, it might be interesting to develop models that are specific to the type of inputs that OMR works on: large images with a high quantity of densely packed objects of various sizes from a vast vocabulary

2. Evaluation: lack of standards for outputting OMR results