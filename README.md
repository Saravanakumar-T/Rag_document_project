# 📄 RAG — Summarize & Q&A

A compact, **local-first** document summarization and Q&A tool for business users.  
Upload multiple documents, build a single knowledge base, generate a short combined summary (5–8 bullets), and ask questions answered **strictly from the uploaded documents**.

---

## 📦 Repository Structure

This repository contains:

- `app.py`  
  Streamlit UI for uploading documents and interacting with the summarizer and Q&A assistant  

- `rag/loader.py`  
  Document loaders and chunking utilities  

- `rag/vectorstore.py`  
  FAISS vector store wrapper and helpers  

- `llm.py`  
  Small LLM interface (prefers local Ollama; OpenAI fallback supported)

---

## 🚀 Quick Overview

- Upload multiple files (PDF, DOCX, PPTX, TXT, HTML, CSV, XLSX, JSON) and treat them as **one knowledge base**.  
- The app:
  - Extracts text  
  - Chunks content  
  - Builds a FAISS vector store (sentence-transformers embeddings)  
  - Generates a single short summary (5–8 concise bullets)  
- Q&A:
  - Retrieves relevant chunks  
  - Answers using **only** the retrieved text  
  - Keeps the summary persistent in the UI (not overwritten by Q&A)

---

## 🦙 Why Ollama?

Ollama provides a straightforward local model hosting experience.

This project prefers a local Ollama model (e.g., `qwen2.5:3b`) for:
- Privacy  
- Low latency  
- Zero API cost  

OpenAI is supported as a fallback when an API key is configured.

---

## 📁 Supported Document Formats

The system supports:

- PDF  
- DOCX  
- PPTX  
- TXT  
- HTML  
- XML  
- JSON  
- CSV  
- XLSX  

All files are converted to cleaned text before being chunked and added to the vector store.

---

## 🔐 Local-First LLM Policy

- The app **prefers Ollama by default** for privacy and speed.  
- If Ollama is unavailable and `OPENAI_API_KEY` is set, the app falls back to OpenAI for inference.

---

## ▶️ Running the Project

### 1️⃣ Prerequisites

- Python 3.10+ (recommended)  
- Ollama installed and running locally (optional, but recommended)  
  👉 https://ollama.com/docs  

Install dependencies:

```powershell
python -m pip install -r requirements.txt
