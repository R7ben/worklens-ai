# WorkLens AI

> An AI-powered productivity toolkit for chatting with PDFs, organizing meeting notes, and improving job applications.

WorkLens AI brings together three practical AI tools in one simple Streamlit app:

- **Chat with your PDF** — upload a document and ask questions about its content.
- **Meeting Notes Assistant** — turn messy notes into summaries, action items, and answers.
- **AI Resume Reviewer** — compare a resume with a job description and receive tailored feedback.

## Features

### 📄 Chat with your PDF

- Upload a PDF document
- Ask questions based on the document content
- Uses Retrieval-Augmented Generation (RAG)
- Retrieves relevant document sections before generating an answer

### 📝 Meeting Notes Assistant

- Summarize raw meeting notes into three clear bullet points
- Extract action items and responsibilities
- Ask custom questions about the meeting content

### 💼 AI Resume Reviewer

- Upload a PDF resume and paste a job description
- Receive a resume-to-job match score out of 100
- Identify matching strengths and missing skills
- Find important keywords missing from the resume
- Get actionable improvement suggestions
- Download the result as a text report

## Tech Stack

| Area | Technology |
| --- | --- |
| Frontend | Streamlit |
| Language | Python |
| LLM Inference | Groq API |
| Model | `llama-3.3-70b-versatile` |
| PDF Processing | PyPDF |
| Retrieval | ChromaDB |
| Environment Variables | python-dotenv |
| Styling | st_yled |

## Getting Started

### Prerequisites

- Python 3.10 or newer
- A [Groq API key](https://console.groq.com/)

### Installation

Clone the repository:

```bash
git clone https://github.com/R7ben/worklens-ai.git
cd worklens-ai
```

Create a virtual environment:

```bash
python -m venv .venv
```

Activate it.

**Windows PowerShell**

```powershell
.venv\Scripts\Activate.ps1
```

**macOS / Linux**

```bash
source .venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Create a `.env` file in the project root:

```env
GROQ_API_KEY=your_groq_api_key_here
```

Run the application:

```bash
streamlit run app.py
```

Open the local URL shown in your terminal, usually:

```text
http://localhost:8501
```

## How PDF Chat Works

1. Upload a PDF document.
2. WorkLens extracts the text using PyPDF.
3. The text is divided into overlapping chunks.
4. ChromaDB finds the most relevant chunks for each question.
5. Groq generates an answer using only the retrieved document context.

> PDF data is temporary and resets when a new file is uploaded or the app restarts.

## Project Structure

```text
worklens-ai/
├── .devcontainer/          # Development container configuration
├── .streamlit/             # Streamlit configuration
├── app.py                  # Main Streamlit application
├── requirements.txt        # Python dependencies
├── .gitignore
└── README.md
```

## Privacy Note

PDFs, resumes, meeting notes, and job descriptions may be processed through the configured AI provider. Do not upload confidential or sensitive personal information unless you understand and accept this.

## Current Limitations

- Supports PDF files only.
- Scanned PDFs without selectable text may not work correctly.
- Uploaded PDF data is not saved between sessions.
- Resume feedback is AI-generated guidance and does not guarantee ATS or hiring outcomes.

## Roadmap

- [ ] Support DOCX and TXT uploads
- [ ] Show source chunks used for PDF answers
- [ ] Add chat history
- [ ] Export meeting summaries and action items
- [ ] Add persistent user workspaces
- [ ] Deploy with secure server-side API key management
- [ ] Add tests and GitHub Actions CI

## Author

Built by [Sapttaruben Krishnan](https://github.com/R7ben), an Applied AI student at UTM Kuala Lumpur.

## License

This is currently a personal learning project. Add a license before commercial use or distribution.
