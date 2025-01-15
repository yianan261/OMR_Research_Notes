1. **OMR and Its Two Primary Tasks**:  
    OMR involves two main tasks:
    
    - **Recovering musical notation** (the visual representation of the score).
    - **Recovering musical semantics** (the meaning or the content of the music, such as pitch, rhythm, and other performance elements). These two tasks help to define different **output categories** for OMR systems.
2. **The Two Broad Areas of OMR Applications**:  
    The authors describe two **overlapping** application areas for OMR outputs. These are:
    
    - **Replayability**
    - **Structured Encoding**

#### 1. **Replayability**:

- **Definition**: Replayability refers to the ability of the system to **recover the music itself** in a form that can be "played back" by a computer. This is achieved by extracting information such as **pitch**, **velocity**, **onset** (timing of notes), and **duration** (how long each note is played).
    
- **Purpose**: In this application, OMR is seen as a component in a larger **music processing pipeline**. Once OMR has extracted the music data, this data can be processed or "played" by a system (like a digital synthesizer or a music program) without the need for human-readable notation.
    
- **Human Readability**: The key point here is that **readability by humans is not required** for replayability. As long as the symbolic data (like MIDI or MusicXML) can be processed and played by a computer, it doesn't matter if it is directly interpretable by humans. This makes it more of an **automated process** focused on **computational playback**.
    
    **Example Use Case**:
    
    - **MIDI** conversion of a scanned music score so that the computer can play the music back. Humans wouldn’t necessarily need to read or interpret the score directly, just the symbolic data.

#### 2. **Structured Encoding**:

- **Definition**: Structured Encoding involves **recovering both the music and the information about how it was encoded** using the elements of **music notation** (such as clefs, time signatures, note stems, rests, etc.).
    
- **Purpose**: This application focuses on **reproducing the score itself**, meaning the OMR system **re-encodes** the music in a way that it can be read by humans, preserving the original **music notation** structure.
    
- **Lossless Re-Encoding**: The goal here is to **reproduce the exact music score**, keeping all the original notation intact. The score can then be **printed** or used for **performance**. The system is required to maintain all the **notation** details exactly as they were in the original score. This would be necessary if the output of OMR needs to be used by musicians who will **read the score directly**.
    
- **Recovering Musical Semantics**: In this case, **musical semantics** (such as understanding what the notes represent in terms of musical meaning) is sometimes less critical. However, **in practice**, it is **desirable** to recover the semantics, as this can help with operations like **transposing** the music (changing the key), which would be useful for performers or in arrangements for different instruments.
    
    **Example Use Case**:
    
    - Converting a scanned handwritten score into a **MusicXML file** that can be used in notation software (like Finale or Sibelius), which preserves the full visual notation and can be printed or edited. Here, the recovery of music semantics helps in tasks like transposing a part for a different instrument.

### Why the Two Categories Matter:

- **Replayability** focuses on **computational music playback** and does not require human-readable notation. It is about getting the symbolic data that a computer can process, play, and manipulate (like converting a sheet of music into MIDI).
    
- **Structured Encoding** focuses on **reproducing the visual score** and **music notation** in a way that can be **read and used by humans**. This is more about preserving the **exact representation of the music** that humans can interpret and perform.
    

### Practical Example:

- If you scan an old, handwritten score:
    - **Replayability** would convert the image into MIDI or some other symbolic representation (e.g., MusicXML) and play it back using a computer.
    - **Structured Encoding** would re-create the score in a **notation software** like Finale, preserving all visual aspects (note shapes, rests, time signatures, etc.) so that a musician can read the score and perform it.