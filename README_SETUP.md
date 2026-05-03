# Real-Time AI Sign Language Generator

A web application that translates voice and text into sign language with support for multiple languages including American Sign Language (ASL), Indian Sign Language (ISL), and regional Indian languages.

## Features

- **Voice-to-Sign Translation**: Real-time speech recognition and conversion to sign language videos
- **Text-to-Sign Translation**: Type text and see sign language representation
- **Multi-language Support**:
  - American Sign Language (ASL)
  - Indian Sign Language (ISL)
  - Hindi Sign Language
  - Telugu Sign Language
  - Gujarati Sign Language
- **Interactive UI**: Real-time translation with adjustable playback speed
- **User Feedback System**: Contribute corrections to improve translations
- **Sentiment Analysis**: Display emotional context of translated content

## Tech Stack

### Backend

- **Framework**: Flask (Python)
- **Speech Recognition**: Vosk (offline speech-to-text)
- **Sentiment Analysis**: TextBlob
- **Sentiment Analysis**: TextBlob
- **Server**: Flask with CORS enabled

### Frontend

- **Framework**: Expo (React Native)
- **Web View**: Embedded Flask app interface
- **Bundler**: Metro

### Data

- **Sign Videos**: MP4 format language videos
- **Sign Images**: ASL alphabet and Indian alphabet images
- **Model Storage**: Vosk language-specific models

## Installation

### Prerequisites

- Python 3.8+
- Node.js 16+
- npm or yarn

### Backend Setup

1. Navigate to the VSTEST1 directory:

```bash
cd VSTEST1
```

2. Create a Python virtual environment:

```bash
python -m venv venv
source venv/Scripts/activate  # On Windows: venv\Scripts\activate
```

3. Install Python dependencies:

```bash
pip install flask flask-cors vosk textblob SpeechRecognition pyaudio
```

4. Download speech recognition models:

```bash
python setup_models.py
```

Models will be installed in:

- `vosk-model-small-en-us-0.15/` (ASL)
- `vosk-model-en-in-0.5/` (ISL)
- `vosk-model-small-hi-0.22/` (Hindi)
- `vosk-model-small-te-0.42/` (Telugu)
- `vosk-model-small-gu-0.42/` (Gujarati)

### Frontend Setup

1. Install dependencies:

```bash
npm install
```

2. Create `metro.config.js` if not present (to avoid nested app conflicts):

```javascript
const { getDefaultConfig } = require("expo/metro-config");
const exclusionList = require("metro-config/src/defaults/exclusionList");

const config = getDefaultConfig(__dirname);
config.resolver.blockList = exclusionList([
  /VSTEST1[\\\/]SignLanguageApp[\\\/].*/,
]);

module.exports = config;
```

## Running the Application

### Start Backend (Terminal 1)

```bash
cd VSTEST1
python app.py
```

Backend runs on: **http://127.0.0.1:5001/**

### Start Frontend (Terminal 2)

```bash
npm run start
```

Frontend serves on: **exp://[YOUR_IP]:8082**

Open your browser to **http://127.0.0.1:5001/** to use the application.

## Project Structure

```
.
├── VSTEST1/
│   ├── app.py                 # Flask backend server
│   ├── voice_to_sign.py       # Speech recognition module
│   ├── sign_translator.py     # Translation logic
│   ├── language_processor.py  # Context analysis
│   ├── setup_models.py        # Model downloader
│   ├── mp4videos/             # Sign language videos
│   ├── alphabetimages/        # ASL alphabet images
│   ├── indianalphabetsandnumbers/  # Indian alphabet images
│   ├── templates/             # HTML templates
│   ├── static/                # CSS & JS assets
│   └── vosk-model-*/          # Downloaded language models
├── App.js                     # Expo/React Native entry point
├── package.json               # Frontend dependencies
├── metro.config.js            # Metro bundler config
└── README.md                  # This file
```

## API Endpoints

- `GET /` - Main application page
- `POST /select_language` - Select translation language
- `GET /start_stream` - Begin speech recognition stream
- `POST /translate_text` - Translate text input
- `POST /upload_sign` - Upload custom sign video

## Environment Variables

No environment variables required for basic setup.

Optional: Configure Flask debug mode in `VSTEST1/app.py`:

```python
app.run(
    host='0.0.0.0',
    port=5001,
    debug=True  # Set to False for production
)
```

## Troubleshooting

### Models not downloading

```bash
cd VSTEST1
python setup_models.py
```

### Port already in use

Change port in `VSTEST1/app.py`:

```python
app.run(host='0.0.0.0', port=5002)  # Use different port
```

### Frontend not connecting to backend

Update backend URL in `App.js`:

```javascript
const serverUrl = "http://YOUR_IP:5001/";
```

## Deployment

### Option 1: Heroku (Free tier deprecated, but guides available)

### Option 2: Render (Free tier available)

### Option 3: Railway

### Option 4: AWS Lambda + API Gateway

See deployment documentation for detailed setup instructions.

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see LICENSE file for details.

## Acknowledgments

- Vosk project for offline speech recognition models
- Sign language communities for resources and guidance
- NISH (National Institute of Speech and Hearing) for ISL resources

## Contact

For questions or suggestions, please open an issue on GitHub.

---

**Created**: May 2026  
**Version**: 1.0.0
