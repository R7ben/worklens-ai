
- Upload a PDF resume and paste a job description.
- Receive a resume-to-job match score out of 100.
- Identify strengths, gaps, missing keywords, and tailored improvement suggestions.
- Download the analysis as a text report.

## Tech Stack

- **Frontend:** Streamlit
- **LLM inference:** Groq API — `llama-3.3-70b-versatile`
- **PDF processing:** PyPDF
- **Retrieval:** ChromaDB
- **Configuration:** python-dotenv
- **Styling:** st_yled

## Getting Started

### Prerequisites

- Python 3.10 or newer
- A [Groq API key](https://console.groq.com/)

### Installation

Clone the repository and enter it:

```bash
git clone https://github.com/R7ben/worklens-ai.git
cd worklens-ai
```

Create and activate a virtual environment:

```bash
python -m venv .venv

# Windows PowerShell
.venv\Scripts\Activate.ps1

# macOS / Linux
source .venv/bin/activate
```

Install the dependencies:

```bash
pip install streamlit st_yled pypdf chromadb python-dotenv groq
```

Create a `.env` file in the project root:

```env
GROQ_API_KEY=your_groq_api_key_here
```

Run the application:

```bash
streamlit run app.py
```

Open the local address shown in the terminal, usually `http://localhost:8501`.

## How Document Chat Works

1. The app extracts text from an uploaded PDF with PyPDF.
2. It splits the text into approximately 500-character chunks with 50-character overlap.
3. ChromaDB embeds and stores the chunks in an in-memory collection.
4. For each user question, the app retrieves the five closest chunks.
5. The retrieved context is sent to Groq with an instruction to answer only from that context.

> The document collection is temporary and resets when a new PDF is uploaded or the app restarts.

## Project Structure

```text
worklens-ai/
├── app.py          # Streamlit application and all three tools
├── .env            # Local API key; never commit this file
├── .gitignore
└── README.md
```

## Current Limitations

- PDF retrieval data is stored only in memory and is not retained between sessions.
- The application currently supports PDF files only.
- Resume analysis is AI-generated guidance, not a guarantee of ATS or hiring outcomes.
- Users should avoid uploading confidential documents unless they understand the privacy implications of sending content to the configured AI provider.

## Roadmap

- Persist document collections per user or workspace.
- Show the source chunks used for each document answer.
- Support DOCX and TXT uploads.
- Add conversation history for document chat.
- Add exportable meeting summaries and action-item lists.
- Deploy the app with a secure server-side API-key configuration.

## Author

Built by [Ruben Krishnan](https://github.com/R7ben), an Applied AI student at UTM Kuala Lumpur.

## License

This is a personal learning project. Add a license before using or distributing it commercially.
