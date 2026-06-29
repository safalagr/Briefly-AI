# Briefly AI 🎙️🧠

> **Your Personal AI-Powered Study Assistant**

**Briefly AI** is a comprehensive, client-side web application designed to revolutionize how students and professionals process information. By leveraging the power of Google Gemini, Briefly AI instantly turns live speech, YouTube videos, and uploaded documents into highly structured study materials: markdown notes, interactive flashcards, practice quizzes, and visual mind maps.

Whether you're sitting in a 2-hour college lecture or trying to summarize a long YouTube tutorial, Briefly AI ensures you never miss a key concept again.

---

## ✨ Comprehensive Feature Set

### 🎤 Live Audio Transcription & Recording
* **Real-Time Processing**: Record lectures directly from your browser. The app captures your microphone input and provides a running transcript.
* **Pause & Resume**: Seamlessly pause your recording during breaks and append new audio to the same session.

### 📺 YouTube Video Integration
* **Auto-Fetch Transcripts**: Paste any YouTube video URL. The app automatically fetches the available captions/transcripts.
* **Multi-Language Support**: If a video has subtitles in multiple languages, you can select which transcript to import.

### 📄 Universal Document Uploads
* **Multi-Format Parsing**: Upload existing study materials. Briefly AI natively extracts text from PDFs (`pdfjs-dist`), Word documents (`mammoth`), and plain text files.
* **Combined Resources**: Upload multiple files at once to synthesize notes across an entire module or course.

### 🤖 Google Gemini AI Generation
Once a transcript or document is loaded, Google Gemini springs into action to generate:
1. **📝 Executive Summaries**: Condenses hours of talking into a quick 1-minute read highlighting the main points.
2. **⚡ Interactive Flashcards**: Generates Q&A style cards. Perfect for active recall and spaced repetition study methods.
3. **🎓 Practice Quizzes**: Automatically constructs multiple-choice questions with feedback to test your comprehension.
4. **📚 Structured Study Notes**: Creates beautiful, cleanly formatted Markdown notes with headings, bullet points, and bolded keywords.
5. **🗺️ Mind Maps**: Generates visual concept maps rendered beautifully via `Mermaid.js` to help visual learners connect the dots.

### 💻 User Experience & Organization
* **🌓 Dark/Light Mode**: Fully responsive UI that respects your system preferences, complete with a manual toggle.
* **🗂️ Categorization**: Automatically or manually tag your lectures (e.g., `#YouTube`, `#Biology101`).
* **🔍 Search Engine**: Instantly search through your entire library of transcripts and AI-generated notes.
* **💾 Local-First Architecture**: All recordings, transcripts, and AI notes are saved directly in your browser's local storage. No backend database required!
* **📤 Export/Import Data**: Never lose your notes. Export your entire library as a portable JSON file and import it on another device.

---

## 🏗️ Project Architecture & Folder Structure

Briefly AI is built using a modern React SPA architecture. Here's a brief overview of the core structure:

```text
briefly-ai/
├── src/
│   ├── components/      # Reusable UI components (Recorder, TranscriptView, FileUploader)
│   ├── services/        # API integrations and business logic
│   │   ├── geminiService.ts   # Handles prompts and API calls to Google Gemini
│   │   ├── youtubeService.ts  # Fetches transcripts via RapidAPI
│   │   └── storageService.ts  # Manages local browser storage and exports
│   ├── App.tsx          # Main application layout and state management
│   ├── types.ts         # TypeScript interfaces for global data structures
│   └── index.css        # Tailwind directives and global styles
├── public/              # Static assets
└── .env.local           # Environment variables (API Keys)
```

---

## 🛠️ Tech Stack & Dependencies

* **Frontend Framework**: [React 19](https://react.dev/) with [TypeScript](https://www.typescriptlang.org/) for robust, scalable UI components.
* **Build Tool**: [Vite](https://vitejs.dev/) for lightning-fast HMR and optimized production builds.
* **Styling**: [Tailwind CSS](https://tailwindcss.com/) for utility-first, highly customizable styling and responsive design.
* **AI Intelligence**: [`@google/genai`](https://ai.google.dev/) (Google Gemini API) for advanced natural language processing and content generation.
* **YouTube API**: [RapidAPI](https://rapidapi.com/) for bypassing standard YouTube API limitations on closed captions.
* **Markdown Parsing**: [`marked`](https://marked.js.org/) to convert AI-generated markdown notes into styled HTML.
* **Diagram Rendering**: [`mermaid`](https://mermaid.js.org/) to dynamically render complex mind maps from text.
* **Document Parsing**: [`pdfjs-dist`](https://mozilla.github.io/pdf.js/), [`mammoth`](https://www.npmjs.com/package/mammoth), and [`jszip`](https://stuk.github.io/jszip/) for client-side file extraction without a backend server.

---

## 🚀 Step-by-Step Setup Guide

Follow these instructions to get a local development environment up and running.

### 1. Clone the repository
```bash
git clone <your-repo-url>
cd briefly-ai
```

### 2. Install dependencies
Make sure you have [Node.js](https://nodejs.org/) (v18+ recommended) installed, then run:
```bash
npm install
```

### 3. Acquire API Keys
To use the core features, you will need two free API keys:
1. **Google Gemini API Key**: Get it from [Google AI Studio](https://aistudio.google.com/).
2. **RapidAPI Key**: Sign up on [RapidAPI](https://rapidapi.com/) and subscribe to a free YouTube Transcript API.

### 4. Set up Environment Variables
Create a file named `.env.local` in the root directory of the project and add your API keys:

```env
# Google Gemini API Key (Required for Summaries, Notes, Flashcards, etc.)
VITE_GEMINI_API_KEY=your_gemini_api_key_here

# RapidAPI Credentials (Required for YouTube Import)
VITE_RAPID_API_KEY=your_rapidapi_key_here
VITE_RAPID_API_HOST=youtube-transcripts.p.rapidapi.com
```

### 5. Start the Development Server
```bash
npm run dev
```
Open [http://localhost:5173](http://localhost:5173) in your browser. The app should now be running locally!

---

## 🐛 Troubleshooting & FAQs

| Issue | Solution |
|-------|----------|
| **"RapidAPI configuration missing"** | Ensure API keys are correctly spelled in `.env.local`, then **restart the dev server** (`npm run dev`). |
| **Microphone not working** | Ensure you are served over `localhost` or `https`. Modern browsers strictly block microphone access on insecure `http` origins. |
| **AI Content failing to generate** | Check your browser's developer console. This is usually caused by an invalid/expired `VITE_GEMINI_API_KEY`, or hitting the free-tier rate limits. |
| **YouTube Import Error** | Verify the YouTube video actually has closed captions (CC) enabled. Videos entirely lacking captions will fail. |
| **Data not saving between reloads** | Ensure you are not browsing in "Incognito/Private" mode, as some browsers clear LocalStorage upon exit. |

---

## 🤝 Contributing
Contributions are always welcome! Whether it's adding new features, fixing bugs, or improving documentation, feel free to open an issue or submit a Pull Request.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License
Distributed under the MIT License.
