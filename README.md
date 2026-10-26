# AI PDF Study Assistant

A local AI-powered study workspace that helps you study from your PDF notes. Upload documents, ask questions in natural language, and get answers grounded in relevant passages from your own files—with page references to help you verify the information.

> **Built with:** Python · Streamlit · Ollama · FAISS · Sentence Transformers

## Features

- **Multiple PDF uploads** — work with more than one PDF in a study session.
- **Semantic search** — find relevant passages by meaning, not just exact keywords.
- **Local AI answers** — generate responses using Ollama and the `llama3.2:3b` model.
- **Page-aware references** — answers can include the source filename and page number.
- **Study chat** — ask follow-up questions about your uploaded material.
- **Source passages** — inspect retrieved excerpts to help check an answer against the original notes.
- **Clean dark interface** — a navy-blue workspace designed for focused study.

## How it works

1. **Upload PDFs** in the Streamlit interface.
2. **Extract and split text** into smaller passages associated with their source pages.
3. **Create embeddings** with the MiniLM Sentence Transformers model.
4. **Retrieve relevant passages** using a FAISS similarity index when you ask a question.
5. **Generate an answer** with your local Ollama model, using the retrieved passages as context.
6. **Review the sources** and open the cited page in your original PDF to verify details.

## Tech stack

| Component | Purpose |
|---|---|
| Python | Application logic |
| Streamlit | Web interface |
| Ollama (`llama3.2:3b`) | Local language model for answers |
| Sentence Transformers (`all-MiniLM-L6-v2`) | Text embeddings |
| FAISS | Similarity search over document chunks |
| PyMuPDF | PDF text extraction |
| Tesseract OCR / Pillow | OCR and image processing support, where configured |

## Requirements

- Windows, macOS, or Linux
- Python 3.10 or newer (use a version supported by the installed dependencies)
- [Ollama](https://ollama.com/) installed and running
- Git (optional, for cloning the repository)

## Setup

### 1. Clone the repository

```bash
git clone https://github.com/sm903-hub/ai-pdf-study-assistant.git
cd ai-pdf-study-assistant
```

### 2. Create and activate a virtual environment

**Windows PowerShell**

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

**macOS / Linux**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

If the repository contains `requirements.txt`, run:

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

If `requirements.txt` is not present yet, install the dependencies listed by the project before starting the app.

### 4. Start Ollama and download the model

```bash
ollama pull llama3.2:3b
```

Make sure the Ollama service is running before you ask the app to generate an answer. The first run may also download the embedding model.

### 5. Run the app

```bash
python -m streamlit run app.py
```

Streamlit will print a local URL in the terminal, usually `http://localhost:8501`. Open that URL in your browser.

## Using the app

1. Open the local Streamlit page.
2. Upload one or more PDF study documents.
3. Wait for the document processing/indexing step to finish.
4. Ask a question about the uploaded content.
5. Review the answer and its source passages/page references.
6. Ask follow-up questions or start a new study session when needed.

## Notes and limitations

- **Verify important answers.** Retrieval-augmented generation can still produce incomplete or incorrect answers. Use the cited source passages and original PDF to check key facts.
- **Scanned PDFs:** text extraction depends on whether the PDF contains selectable text. OCR may be needed for image-only pages and depends on the local OCR setup.
- **Local model performance:** answer speed and quality depend on your hardware and the Ollama model available on your machine.
- **Privacy:** document processing and answer generation are intended to run locally with the configured models. Review the code and any installed integrations to confirm the behavior of your own setup.

## Project status

This is a learning project under active development. Features and interface details may change as the project improves.

## Repository

[github.com/sm903-hub/ai-pdf-study-assistant](https://github.com/sm903-hub/ai-pdf-study-assistant)

## License

No license has been specified yet. Unless a license is added to the repository, reuse and redistribution are not automatically granted.
