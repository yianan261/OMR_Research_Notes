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
[[OMR Definition diagram]]

1. Optical Music Recognition is a field of research that investigates how to computationally read music notation in documents. computer should read the music

From a technical point of view, OMR can be considered a subfield of computer vision and document analysis, with deep learning acting as a catalyst that opens up promising novel approaches. Within the context of Music Information Retrieval (MIR), OMR should enable the application of MIR algorithms that rely on symbolic data and audio inputs (through rendering the recognized scores).

OMR has practical implications for composers, conductors, and the performers themselves, as it cuts down the costs of digitizing scores, and therefore bring the benefits of digital formats to their everyday practice.

## music to document

Music can be conceptualized as a structure of _notes in time →_ the conceptualization we consider for the purpose of OMR

## note definition

A note is a musical object that is defined by four parameters: _pitch, duration, loudness_, and _timbre_. Additionally, it has an _onset_: a placement onto the axis of time, which in music does not mean wall-clock time, but is measured in relative units called beats.

## music notation system definition

A music notation system is a visual language that aims to encode music into a graphical form and enrich it with information on _how to perform_ it (e.g., bowing marks, fingerings, or articulations)

### current system
Common Western Music Notation (CWMN, also known as modern staff notation), which evolved during the seventeenth century from its mensural notation predecessors and stabilized at the beginning of the nineteenth century.



