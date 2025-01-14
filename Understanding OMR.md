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




