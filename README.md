# Arslan – Auditory Interaction System  
*(Offline Speech Pipeline – C# Prototype)*

## Overview
This repository documents the **auditory interaction subsystem** developed for **Arslan**, a humanoid robot prototype created as a **Computer Engineering graduation project**.

I was responsible for designing and implementing a **fully offline voice interaction pipeline**, enabling Arslan to listen, understand, respond, and speak back to users under strict academic, technical, and tooling constraints.

This project was not about building a polished commercial product.  
It was about **engineering judgment, resilience, and system integration** in a constrained environment.

---

## What This System Does
The auditory subsystem enables Arslan to:

- Capture spoken user input via microphone  
- Perform **offline speech-to-text** processing  
- Generate context-aware responses  
- Optionally translate responses into another language  
- Deliver spoken feedback using text-to-speech  
- Operate **without cloud services or internet dependency**

The entire pipeline was designed to be **modular, inspectable, and adaptable** to future embedded hardware.

---

## High-Level Workflow
1. User speaks  
2. Audio is captured and buffered  
3. Speech is transcribed locally (STT)  
4. Text is routed to a local chatbot or data source  
5. Optional translation is applied  
6. Response is spoken aloud (TTS)  
7. System loops for continuous interaction  

This architecture isolates responsibilities, making the system easier to debug, extend, and evolve.

---

## System Design & Visual Documentation
To clearly communicate the system design, this repository includes structured visual documentation in the **`/docs`** directory:

- **`/docs/diagrams/`**
  - Auditory interaction flowchart  
  - Auditory system objectives diagram  

- **`/docs/screenshots/`**
  - Windows Forms interface  
  - Console output showing live transcription and Arslan’s responses  

Each folder contains its own README explaining what the visuals represent and how they relate to the system pipeline.

---

## Technologies & Engineering Choices

### Programming Language & Environment
- **C# (.NET Framework)**  
- **SharpDevelop IDE**

> SharpDevelop was imposed as an academic constraint. While outdated, it required manual dependency handling and low-level architectural decisions, significantly increasing the engineering complexity of the project.

---

### Speech Recognition (Offline)
- **Vosk**

Chosen for:
- Offline operation  
- Privacy preservation  
- Compatibility with robotic and embedded contexts  

Audio was processed in **16 kHz mono**, matching Vosk’s required input format.

---

### Audio Capture
- **NAudio**

Used for:
- Microphone access  
- Audio buffering  
- Format control prior to transcription  

---

### Voice Output
- **System.Speech.Synthesis**

Used to generate spoken responses with adjustable rate and volume.

---

### Translation
- **LibreTranslate (Docker, Localhost)**

A locally hosted translation service was integrated to demonstrate multilingual capability **without external APIs**, ensuring full offline operation and data privacy.

---

### Knowledge & Data Handling
- **JSON-based local knowledge storage**

Due to tooling and database integration limitations, structured **JSON files** were used to store real-world data (e.g., hospitals, locations).

This allowed Arslan to answer questions such as:
> “Where is the nearest hospital?”

The system remains modular, allowing future migration to database-backed storage without redesigning the auditory pipeline.

---

## Selected Code Excerpts (Illustrative)

> Full source code and third-party libraries are **not publicly shared** due to licensing, ownership, and academic integrity considerations.  
> The following excerpts illustrate core logic only.

### Local Translation via HTTP (LibreTranslate)
```csharp
var payload = new {
    q = text,
    source = "en",
    target = "fr",
    format = "text"
};

string json = JsonConvert.SerializeObject(payload);
HttpResponseMessage response = await client.PostAsync(
    apiUrl,
    new StringContent(json, Encoding.UTF8, "application/json")
);

string responseJson = await response.Content.ReadAsStringAsync();
## Code Excerpts Overview

These excerpts demonstrate:

- Offline STT integration  
- JSON parsing  
- Asynchronous HTTP communication  
- Modular processing stages  

---

## Challenges Faced (and Solved)

This subsystem was developed under **non-ideal conditions**:

- Outdated IDE and toolchain  
- Manual DLL compatibility management  
- High latency during early iterations  
- Asynchronous audio state handling  
- Limited access to final robot hardware  

Despite these challenges, the system achieved **stable, functional auditory interaction**, with response times reduced from **over one minute** to approximately **30 seconds** in the final prototype.

---

## Academic Context

This work was developed as part of a **Computer Engineering graduation project**.

Each team member was responsible for a distinct subsystem:

- Audio interaction (**this repository**)  
- Vision  
- Motion control  
- Data security  
- Hardware integration  

This repository documents **my individual contribution** to the overall project.

---

## Future Improvements

Potential extensions and refinements include:

- Migration to a modern IDE and runtime  
- Streaming speech recognition for lower latency  
- Embedded hardware deployment  
- Database-backed knowledge systems  
- Advanced dialogue management  

---

## Author

**Hadil Zahiri**  
Computer Engineering – Graduation Project

