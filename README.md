# WorkLens AI

**WorkLens AI** is a Streamlit-powered AI workspace for understanding documents, turning meeting notes into clear next steps, and improving resume-to-job matches.

It brings three practical tools into one interface:

- **Document Chat** — upload a PDF and ask questions grounded in its contents.
- **Meeting Insights** — turn raw meeting notes into summaries, action items, or answers to specific questions.
- **Resume Match Analyzer** — compare a resume with a job description and receive an AI-generated match score, strengths, gaps, and suggested keywords.

## Why WorkLens AI?

Professional information is often trapped in long documents, rough notes, and job descriptions. WorkLens AI helps users turn that information into useful, actionable insights without switching between separate tools.

## Features

### Document Chat

- Upload and preview a PDF in the browser.
- Extract and split document text into overlapping chunks.
- Store chunks in a temporary ChromaDB collection.
- Retrieve the five most relevant chunks for each question.
- Generate answers with Groq's `llama-3.3-70b-versatile` model using only retrieved document context.

### Meeting Insights

- Paste unstructured meeting notes.
- Generate a concise three-bullet summary.
- Extract action items and responsibilities.
- Ask custom questions about the supplied notes.

### Resume Match Analyzer

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
