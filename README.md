# AI-Based Court Hearing Transcription with Speaker Diarization

This project implements an end-to-end pipeline for **automatic transcription of court hearing videos**, including **audio extraction, speech-to-text transcription, speaker diarization, and timestamps**.

It is designed to support **legal professionals**, researchers, and developers who need to analyze long hearing recordings and convert them into structured textual documents.
This project implements an end-to-end pipeline for automatic transcription of court hearing videos, including audio extraction, speech-to-text transcription, speaker diarization, and timestamps.

## Features

- Accepts **single video files or folders** with multiple `.mp4` files
- Automatic **audio extraction and normalization** (FFmpeg)
- **Speech-to-text transcription** using AssemblyAI
- **Speaker diarization** (who spoke and when)
- **Timestamps per utterance**
- Outputs:
  - Literal transcription (`.txt`)
  - Diarized transcription with timestamps (`.txt`)
  - Raw API response (`.json`) for auditing or further processing
- Ready to scale from notebooks to web applications

## Technologies Used

- **Python**
- **FFmpeg** – audio extraction and preprocessing
- **AssemblyAI API** – transcription + diarization + timestamps
- **Kaggle** – experimentation and prototyping environment

## Pipeline Overview

Video (.mp4)

↓

Audio Extraction & Normalization (FFmpeg)

↓

AssemblyAI Transcription API

├── Speech-to-text

├── Speaker diarization

└── Timestamps

↓

Structured Outputs (.txt / .json)

## Output Format

### Diarized Transcription (`*_assemblyai_diarized.txt`)

Example:

```
[00:05:12 - 00:05:27] SPEAKER_0: Good afternoon, I declare the hearing open.
[00:05:28 - 00:05:35] SPEAKER_1: Your Honor, speaking for the plaintiff.
```

Each block contains:
- Start and end timestamps
- Speaker label (automatically assigned)
- Transcribed text

## Important Notes

- Speaker labels are **generic** (e.g., `SPEAKER_0`, `SPEAKER_1`)
- Mapping speakers to legal roles (Judge, Plaintiff’s Lawyer, Defendant, etc.)
  is a **planned future enhancement**
- Human review is recommended for legal or official use

## API Key Configuration

This project uses the **AssemblyAI API**.

For security reasons, the API key is **not stored in the code**.

### Kaggle Setup
1. Go to **Add-ons → Secrets**
2. Create a secret:
   - **Key:** `ASSEMBLYAI_API_KEY`
   - **Value:** your AssemblyAI API key
3. Restart the notebook session

## How to Run

1. Set the input path:
```python
INPUT_PATH = Path("/kaggle/input/your-video-or-folder")
```
2. Run the notebook cells in order
3. Generated files will be saved to: /kaggle/working/transcricoes/

## Future Improvements (Planned)

- Legal role mapping (e.g., `SPEAKER_0 → Judge`)
- Export formats for legal workflows (`.docx`, `.pdf`)
- Streamlit web application (upload → transcribe → download)
- Batch processing with role templates
- Automatic summarization of hearings
- Redaction of sensitive information

## Use Cases

- Court hearing analysis
- Legal document preparation
- Academic research on judicial proceedings
- AI-assisted legal workflows
- Audio/video archiving and indexing

# Author
Developed by Ana Dognini

Focus: AI, Data Science, and applied machine learning in real-world contexts
