# RAG-app — PDF → Vector DB → LLM (RAG) pipeline

This repository contains a Jupyter notebook (`notebook/pdf_loader.ipynb`) that demonstrates a simple Retrieval-Augmented Generation (RAG) pipeline:

- Ingest PDFs into LangChain documents.
- Split documents into chunks with `RecursiveCharacterTextSplitter`.
- Create embeddings with `sentence-transformers` and store them in ChromaDB.
- Retrieve relevant context and generate answers with a Groq LLM (`ChatGroq`).

Prerequisites
- Python 3.8+ (project requires 3.13 in pyproject; use a matching environment).
- Git, Java (optional, for BFG), and access to the Groq API if using `ChatGroq`.

Install

```bash
python -m venv .venv
source .venv/Scripts/activate  # Windows PowerShell: .venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

Quick Start
1. Add your PDFs to `data/pdf/`.
2. Open `notebook/pdf_loader.ipynb` in VS Code or Jupyter and run cells top-to-bottom.
3. If you want to persist the vector store, ensure `data/vector_store/` is writable.

Environment variables
- `GROQ_API_KEY` — required for Groq LLM calls. Example (PowerShell):

```powershell
$Env:GROQ_API_KEY = "your_groq_api_key"
```

Important files
- `notebook/pdf_loader.ipynb` — main pipeline notebook.
- `requirements.txt` / `pyproject.toml` — dependencies.
- `.gitignore` — ignores secrets, virtualenvs, and ChromaDB data (created).

Common issues & fixes
- Secret accidentally committed: rotate the secret immediately and remove it from Git history (use BFG or `git filter-repo`).
- `Path` not defined: ensure the first cell imports `from pathlib import Path`.
- Groq model decommissioned (400): pick a supported model; update `model_name` used by `ChatGroq`.
- Embedding/Chroma errors: ensure embeddings are a 2D list of Python floats before calling `collection.add()`.

Tips
- Keep `.env` out of Git (see `.gitignore`). Use environment variables or a secrets manager.
- Batch large `add_documents` calls when adding many documents to the vector DB.

If you want, I can:
- Run the notebook cells to validate the pipeline locally (requires dependencies and GROQ key).
- Provide commands to safely purge secrets from the repository history.

----
Generated from `notebook/pdf_loader.ipynb`.
----
Generated from `notebook/pdf_loader.ipynb`.
