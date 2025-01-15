# current challenges
few introductory materials available, researchers might not have enough musical background

OMR has not defined its goals with sufficient rigor to formulate its motivating applications clearly, in terms of inputs and outputs. Work on OMR is thus fragmented
# aims:

1. provide robust definition of OMR and relationship to related fields
2. analyze how OMR inverts musical encoding process to recover musical notation and musical semantics from documents
3. propose taxonomy of OMR
4. discusses how deep learning affects modern OMR research

The primary contributions of this paper are to clearly define what OMR is, what problems it seeks to solve and why.1 OMR is, unfortunately, a somewhat opaque field due to the fusion of the music-centric and document-centric perspectives

The paper addresses certain shortcomings in current literature: • A robust definition of what OMR is, and a thorough analysis of its inherent structure; • Terminological clarifications that should make the field more accessible and easier to survey;

- A review of OMR uses and applications; well-defined in terms of inputs and outputs, and—as much as possible—recommended evaluation methodologies;
    
- A brief discussion of how OMR was traditionally approached and how modern machine learning techniques (namely deep learning) affect current and future research;
    
- As supplementary material, an extensive, extensible, accessible, and up-to-date bibliography of OMR
    (see Appendix A: OMR Bibliography).

# definition
[[understandingOMR.pdf#search=Definition 1. Optical Music Recognition is a field of research that investigates how to computationally read music notation in documents. The first claim of this definition is that OMR is a research field. In the published literature, many authors refer to OMR as “task” or “process,” which is insufficient, as OMR cannot be properly formalized in terms of unique inputs and outputs (as discussed in Section VI). OMR must, therefore, be considered something bigger, like the embracing research field, which investigates how to provide a computer with the ability to read music notation. Within this research field, several tasks can be formulated with specific, unambiguous input-output pairs|understandingOMR, p.3]]

1. Optical Music Recognition is a field of research that investigates how to computationally read music notation in documents. computer should read the music

From a technical point of view, OMR can be considered a subfield of computer vision and document analysis, with deep learning acting as a catalyst that opens up promising novel approaches. Within the context of Music Information Retrieval (MIR), OMR should enable the application of MIR algorithms that rely on symbolic data and audio inputs (through rendering the recognized scores).

OMR has practical implications for composers, conductors, and the performers themselves, as it cuts down the costs of digitizing scores, and therefore bring the benefits of digital formats to their everyday practice.
![[understandingOMR 3.webp]]
[[understandingOMR.pdf#page=4&rect=41,413,583,754|understandingOMR, p.4]]

## music to document

Music can be conceptualized as a structure of _notes in time →_ the conceptualization we consider for the purpose of OMR

## note definition

A note is a musical object that is defined by four parameters: _pitch, duration, loudness_, and _timbre_. Additionally, it has an _onset_: a placement onto the axis of time, which in music does not mean wall-clock time, but is measured in relative units called beats.

## music notation system definition

A music notation system is a visual language that aims to encode music into a graphical form and enrich it with information on _how to perform_ it (e.g., bowing marks, fingerings, or articulations)
### current system
Common Western Music Notation (CWMN, also known as modern staff notation), which evolved during the seventeenth century from its mensural notation predecessors and stabilized at the beginning of the nineteenth century.
## ways to interpret the term "read" in reading music notation
1. recover music notation and information from the engraving process (requires output representation that's capable of storing music notation, e.g. MusicXML or MEI)
2. Recover musical semantics -> notes represented by their pitches, velocities, onsets, durations. "Semantics" here refer to information that can be unambiguously inferred from music notation documents (like MIDI as an output rerpresentation)
## Alternative names of OMR
Alternative names that might not exhibit this vagueness are Optical Music Notation Recognition, Optical Score Recognition, or Optical Music Score Recognition.

## relation to other fields
![[Pasted image 20250114122238.png]]

[[understandingOMR.pdf#page=7&rect=123,261,500,531|understandingOMR, p.7]]

## OMR v.s. OCR
[[understandingOMR.pdf#search=A. Optical Music Recognition vs. Text Recognition|understandingOMR, p.8]]
not the same because music notation is contextual writing system, it's alphabet consists of well-defined primitives (stems, noteheads, flags), how they are placed and arranged on staves affects how they're played
Also the application domain is different, it's in music
in music the interpretation could also vary (e.g. jazz v.s. classical styles/interpretations)

## Optical Music Recognition vs. Other Graphics Recognition Challenges
One thing that makes CWMN more complex than many graphics recognition challenges like mathematical formulae recognition is the complex typographical alignment of objects.
simultaneous events should have the same horizontal position, or each space between multiple notes of the same length should be equal. Interactions between individual objects can force other elements to move around, potentially breaking those principles (e.g. notes in chord could be shifted differently in different compositions to avoid overlappings)
![[understandingOMR 1.webp]]
[[understandingOMR.pdf#page=10&rect=36,444,572,757|understandingOMR, p.10]]

## OMR inputs
online and offline OMR
[[understandingOMR.pdf#search=offline OMR operates on a static image, while online OMR processes music notation as it is being written, e.g., by capturing the stylus input on an electronic tablet device [72], [73], [152], [31]. Online OMR is generally considered easier since the decomposition into strokes provides a high-quality over-segmentation essentially for free|understandingOMR, p.11]]
**Offline OMR includes**:
- **Printed music scores** (e.g., professionally typeset sheet music from music publishers).
- **Handwritten music scores** (e.g., handwritten by composers or musicians).
- **Manuscripts** (old or historical music notation, such as medieval or Renaissance manuscripts, which may be handwritten or printed in earlier styles).
- **Handwritten notation on pre-printed staff paper** (e.g., a composer writing on blank sheet music).
The paper focuses on offline 

### Taxonomy
four categories of structural complexity
[[understandingOMR.pdf#search=(a) Monophonic: only one note (per staff) is played at a time. (b) Homophonic: multiple notes can occur at the same time to build up a chord, but only as a single voice. (c) Polyphonic: multiple voices can appear in a single staff. (d) Pianoform: scores with multiple staves and multiple voices that exhibit significant structural interactions. They can be much more complex than polyphonic scores and cannot be disassembled into a series of monophonic scores, such as in polyphonic renaissance vocal part books|understandingOMR, p.12]]

![[understandingOMR 4.webp]]

[[understandingOMR.pdf#page=13&rect=34,324,586,754|understandingOMR, p.13]]

## OMR outputs

> ([[understandingOMR.pdf#page=13&selection=25,11,26,42|As pointed out by [29], [84], [81], there is still no good way at the moment of how to measure and compare the performance of OMR systems]])
>

Replayability and Structured encoding
> ([[understandingOMR.pdf#page=14&selection=52,0,64,95&color=yellow|understandingOMR, p.14]])
>  • Replayability: recovering the encoded music itself in terms of pitch, velocity, onset, and duration. This application area sees OMR as a component inside a bigger music processing pipeline that enables the system to operate on music notation documents as just another input. Notice that readability by humans is not required for these applications, as long as the computer can process and “play” the symbolic data. 
>  • Structured Encoding: recovering the music along with the information on how it was encoded using elements of music notation. This avenue is oriented towards providing the score for music

* for our project we're concerned with the **replayability** (extraction of music from score to a form that can be played back by computer, without requiring the output to be human-readable); whereas **Structured Encoding** is about extracting both the music and **how it was encoded** visually, preserving the **human-readable notation** for purposes like printing, editing, or performance.
### Level of comprehension
![[understandingOMR 5.webp]]
[[understandingOMR.pdf#page=15&rect=41,360,572,522&color=yellow|understandingOMR, p.15]]

> ([[understandingOMR.pdf#page=17&selection=16,0,44,72&color=red|understandingOMR, p.17]])
> 3) Replayability: Replayability applications are concerned with reconstructing the notes encoded in the music notation document. Notice that producing an actual audio file is not considered to be part of OMR, despite being one of the most frequent use-cases of OMR. In any case, OMR can enable these applications by recovering the pitches, velocities, onsets, and durations of notes. This symbolic representation, usually stored as a MIDI file, is already a very useful abstraction of the music itself and allows for plugging in a vast range of computational tools such as: • synthesis software to produce an audio representation of the composition • music information retrieval tools that operate on symbolic data • tools that perform large-scale music-theoretical analysis • creativity-focused applications [164] Definition 4. Replayability refers to a class of Optical Music Recognition applications that recover sufficient information to create an audible version of the written music.

- **Replayability** in OMR refers to the process of **converting** a **scanned or photographed music score** (the **image** of the notation) into a **machine-readable symbolic format**, typically something like a **MIDI file**. This symbolic representation includes essential information such as:
    - **Pitches** (the notes),
    - **Velocities** (how hard the note is played),
    - **Onsets** (the timing of the note),
    - **Durations** (how long the note is played).
- **OMR itself** does not directly handle the production of audio files. Instead, it focuses on the **conversion of visual notation** into a symbolic format that can be processed computationally. Once this **symbolic data** (like MIDI) is generated, it can be used in other applications to produce an audio version of the music, but this is considered a separate step outside the direct scope of OMR.
-
> ([[understandingOMR.pdf#page=17&selection=47,28,49,13&color=red|understandingOMR, p.17]])
> Many applications have been envisioned that only require replayability. For example, applications that can sight-read the scores to assist practicing musicians by providing missing accompaniment

> ([[understandingOMR.pdf#page=18&selection=4,0,5,53&color=red|understandingOMR, p.18]])
> Once a system is able to arrive at a MIDI-like representation, evaluating the results is a matter of comparing sequences of pitch-onset-duration-triplets.

> ([[understandingOMR.pdf#page=18&selection=9,56,10,105&color=red|understandingOMR, p.18]])
> : the most obvious inadequacy of MIDI is its inability to distinguish pitches that sound equivalent but are named differently, e.g., F-sharp and G-flat

### similarity metrics
> ([[understandingOMR.pdf#page=18&selection=13,0,20,85&color=red|understandingOMR, p.18]])
> Multiple similarity metrics for comparing MIDI files have been proposed during the Symbolic Melodic Similarity track of the Music Information Retrieval Evaluation eXchange (MIREX),15 e.g., by determining the local alignment between the geometric representations of the melodies [156], [157], [158], [155]. Other options could be multi-pitch estimation evaluation metrics [17], Dynamic Time Warping [54], or edit distances between two time-ordered sequences of pitch-duration pairs [165], [33]

#### Geometric representation of music in pitch and time 

The **geometric representation of the pitch-time plane** is a way of visualizing and comparing melodies using **two-dimensional space**, where one axis represents **time** and the other represents **pitch**.

##### Breaking it down:

- **Pitch**: The perceived frequency of a musical note, usually represented in musical notation as the height of the note. Higher pitches correspond to notes with higher frequencies, and lower pitches correspond to notes with lower frequencies.
    
- **Time**: The timing or duration of a musical note, typically represented in sheet music as the position of the note on the horizontal axis (from left to right) or the length of the note.

### Pitch-Time Plane

Imagine a **2D graph** where:

- The **horizontal axis** represents **time** (e.g., when a note is played, its position on the axis tells you its timing relative to other notes).
- The **vertical axis** represents **pitch** (e.g., the note's pitch, higher for higher notes and lower for lower ones).

In this **pitch-time plane**, each note is represented as a point or a small curve:

- **The x-coordinate** of the point tells you when the note is played (its **onset time**).
- **The y-coordinate** of the point tells you the note's pitch (how high or low it is).

### Example:

Consider a simple melody with three notes:

- **Note 1**: C4 (Middle C), played at time 0 (the beginning of the piece).
- **Note 2**: E4, played at time 1.
- **Note 3**: G4, played at time 2.

In the pitch-time plane:

- The **x-coordinate** of each note corresponds to its **time** of occurrence (0, 1, 2).
- The **y-coordinate** corresponds to its **pitch** (e.g., C4 is lower than E4, and E4 is lower than G4).

The points in the pitch-time plane might look something like this:

|Time|C4|E4|G4|
|---|---|---|---|
|0|(0, C4)|||
|1||(1, E4)||
|2|||(2, G4)|

If you plot them on a graph, you'll get points that lie at different positions along the **time axis (x-axis)** and at different **heights (y-axis)** based on pitch.

### Why Geometric Representation?

The geometric representation is useful for comparing melodies because it **turns a sequence of musical notes into a visual, spatial representation**. By looking at the **curves** (or **lines connecting the notes**), you can see the **contour of the melody** — how it rises and falls in pitch over time.

In the context of the paper you mentioned:

- The **notes** are treated as **points** or **curves** on the pitch-time plane.
- **Interpolation** (fitting a smooth curve through these points) is used to model the melody as a **smooth curve**.
- This curve can then be compared to other melodies by measuring how **similar** their **shapes** or **derivatives** are in the pitch-time plane.
### Geometric Representation in Action:

- For example, if you have two melodies, one that rises in pitch steadily and one that oscillates up and down, their **curves** in the pitch-time plane will look different. This visual difference can help the system assess how **similar** or **different** the two melodies are, based on their shape, timing, and pitch changes.
### Summary:

- **Pitch-time plane** is a 2D space where one axis represents **time** and the other represents **pitch**.
- Melodies can be visualized as **points or curves** in this plane.
- This representation helps compare melodies by evaluating their **geometric shape**, which is useful in tasks like **melodic similarity**.
### Conveying musical semantics 
> ([[understandingOMR.pdf#page=18&selection=47,0,54,1&color=red|understandingOMR, p.18]])
> Note that the difference between replayability and structured encoding can seem vague: for instance, imagine a system that detects all notes and all other symbols and exports them into a MusicXML file. The result, however, is not the structured encoding unless the system also attempts to preserve the information on how the scores were laid out. That does not mean it has to store the bounding box and exact location of every single symbol, but the engraving information that conveys musical semantics,

> [!PDF|234, 82, 82] [[understandingOMR.pdf#page=19&annotation=1005R|understandingOMR, p.19]]
> > e.g., with MIDI) is similar to storing a piece of writing in a plain text file; whereas representing music with music notation (e.g., with MusicXML) is similar to a structured description like an HTML website. By analogy, obtaining the structured encoding from the image of a music score can be as challenging as recovering the HTML source code from the screenshot of a website.
> 
> 
