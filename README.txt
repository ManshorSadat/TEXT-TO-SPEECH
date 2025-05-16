# Text-to-Speech Transcription System

## Overview

This project provides a real-time speech-to-text transcription system with speaker diarization, timestamps, keyword extraction, and call duration calculation. It consists of a Python-based backend service using FastAPI and transcription engines (AssemblyAI and OpenAI Whisper), and a desktop GUI client built with PyQt5. A React frontend is planned for future UI enhancements.

## Key Features

* **Real-time transcription:** Streams audio chunks during recording and displays live transcription.
* **Speaker diarization:** Identifies and labels different speakers in the conversation.
* **Timestamps & call duration:** Shows timestamps for each segment and the total duration at the end.
* **Keyword extraction:** Highlights key terms from the conversation.
* **Multiple transcription engines:** Supports both AssemblyAI and Whisper for flexibility.
* **Optional Twilio integration:** Allows phone call transcription through Twilio APIs.
* **Database support:** Originally uses MongoDB; migrating to Qdrant vector database for efficient search.

## Architecture

```
[User Microphone] --> [PyQt5 GUI] --audio chunks--> [FastAPI Backend]
      |                                        |
      +-- live transcript display              +-- Transcription Engines (AssemblyAI / Whisper)
                                               +-- Keyword Extraction (KeyBERT)
                                               +-- Speaker Diarization
                                               +-- Database (MongoDB / Qdrant)
```

## Installation

1. **Clone the repository**:

   ```bash
   git clone https://github.com/yourusername/text-to-speech-transcription.git
   cd text-to-speech-transcription
   ```
2. **Create a virtual environment**:

   ```bash
   python3 -m venv venv
   source venv/bin/activate   # macOS/Linux
   venv\\Scripts\\activate    # Windows
   ```
3. **Install dependencies**:

   ```bash
   pip install -r requirements.txt
   ```
4. **Set up environment variables** in a `.env` file:

   ```ini
   ASSEMBLYAI_API_KEY=your_assemblyai_key
   OPENAI_API_KEY=your_openai_key  # for Whisper
   MONGODB_URI=mongodb://localhost:27017/transcriptions
   QDRANT_URL=http://localhost:6333
   TWILIO_ACCOUNT_SID=your_sid          # optional
   TWILIO_AUTH_TOKEN=your_auth_token    # optional
   ```

## Usage

1. **Start the backend server**:

   ```bash
   uvicorn app.main:app --reload
   ```
2. **Run the desktop GUI client**:

   ```bash
   python gui/main.py
   ```
3. **(Optional) Start React frontend**:

   ```bash
   cd react-frontend
   npm install
   npm start
   ```

## Configuration

* **Switch transcription engine** in `app/config.py`:

  ```python
  TRANSCRIBE_ENGINE = "assemblyai"  # or "whisper"
  ```
* **Enable/disable diarization or keyword extraction** in `app/settings.py`.

## Contributing

1. Fork the repository.
2. Create a new feature branch: `git checkout -b feature-name`.
3. Commit your changes: `git commit -m "Add feature"`.
4. Push to the branch: `git push origin feature-name`.
5. Open a Pull Request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
