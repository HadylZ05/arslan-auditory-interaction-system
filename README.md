# Arslan – Auditory Interaction System

## Project Overview
This repository documents the **auditory interaction subsystem** developed for *Arslan*, a humanoid robot prototype created as a graduation project in Computer Engineering.

The system enables Arslan to:
- Capture spoken user input
- Perform **offline speech recognition**
- Generate contextual responses
- Translate responses into another language
- Deliver spoken feedback through text-to-speech

The focus of this module is **robust audio interaction under constrained development conditions**, rather than commercial deployment.

---

## System Objectives
The primary objectives of the auditory system were:

- Enable **natural voice-based interaction** with users  
- Operate **entirely offline** to ensure privacy and independence from cloud services  
- Support **multilingual responses** (e.g., English → French)  
- Integrate seamlessly with other robot subsystems (vision, motion, security)  
- Remain modular and transferable to embedded robot hardware  

---

## Auditory System Architecture
The auditory pipeline follows a sequential but asynchronous workflow:

1. User speaks
2. Microphone captures raw audio
3. Audio is processed and converted to text (Speech-to-Text)
4. Text is analyzed and routed to a local chatbot or data source
5. Optional translation is applied
6. Final response is vocalized via Text-to-Speech
7. System loops for continuous interaction

This design minimizes dependency coupling and allows individual components to be improved independently.

---

## Technologies Used

### Programming Language & Environment
- **C# (.NET Framework)**
- **SharpDevelop IDE**

> SharpDevelop was mandated by the academic supervisor to encourage low-level problem solving and system understanding under limited tooling. While outdated, it provided a controlled environment that required manual dependency management and explicit architectural decisions.

---

### Speech Recognition
- **Vosk (Offline Speech Recognition Engine)**

Vosk was selected due to its:
- Offline operation
- Multi-language support
- Suitability for embedded and robotic systems

Audio was captured in **16 kHz mono format**, compatible with Vosk’s requirements.

---

### Audio Capture
- **NAudio (.NET Audio Library)**

Used for:
- Microphone device detection
- Real-time audio streaming
- Buffering and format control

---

### Voice Output
- **System.Speech.Synthesis**

Features:
- Text-to-speech generation
- Adjustable speech rate and volume
- Support for SSML in advanced scenarios

---

### Translation
- **LibreTranslate (Docker, Localhost)**

- Operated as a local HTTP service
- Enabled multilingual interaction without external APIs
- Ensured offline functionality and data privacy

---

### Chatbot & Data Handling
- **Local chatbot API (localhost server)**
- **JSON-based place data storage**

Due to database integration constraints within SharpDevelop and team-wide tooling limitations, structured **JSON files** were used to store real-world location data (e.g., hospitals, restaurants).

This allowed Arslan to answer questions such as:
> “Where is the nearest hospital?”

---

## Functional Capabilities
- Offline voice recognition
- Context-aware response generation
- Multilingual spoken feedback
- Continuous interaction loop
- Modular subsystem integration

---

## Development Constraints & Challenges
Several real-world challenges influenced the final system design:

- Outdated IDE limitations (SharpDevelop)
- Manual dependency handling
- Latency in speech recognition and response generation
- Asynchronous audio state management
- Limited hardware testing (laptop microphone/speakers)

Despite these constraints, the system achieved stable and functional auditory interaction.

---

## Academic Context
This project was developed as part of a **Computer Engineering graduation project**.

Each subsystem (audio, vision, motion, data security, hardware) was handled independently by different team members.  
This repository focuses **exclusively on the auditory interaction module**.

Source code and third-party libraries are **not publicly shared** to respect academic integrity and software licensing.

---

## Future Work
Potential improvements include:
- Migration to modern development environments
- Database-backed knowledge systems
- Latency optimization
- Full deployment on embedded robot hardware
- Enhanced dialogue management

---

## Author
Developed by **Hadil Zahiri**  
Computer Engineering – Graduation Project

