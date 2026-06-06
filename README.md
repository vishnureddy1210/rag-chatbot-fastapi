# 🤖 RAG PDF Chatbot

> Upload a PDF and ask questions about it — powered by LangChain, FAISS, and Groq LLM.

[![HuggingFace Space](https://img.shields.io/badge/🤗%20HuggingFace-Live%20Demo-blue)](https://huggingface.co/spaces/vishnuvardhanreddy12/rag-chatbot-fastapi)
[![Python](https://img.shields.io/badge/Python-3.11-yellow?logo=python)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.100+-green?logo=fastapi)](https://fastapi.tiangolo.com/)
[![Docker](https://img.shields.io/badge/Docker-ready-blue?logo=docker)](https://www.docker.com/)

---

## 📖 Overview

This is a Retrieval-Augmented Generation (RAG) chatbot that lets you:

1. **Upload** any PDF document
2. **Ask** questions about its contents in natural language
3. **Get** accurate, context-aware answers powered by an LLM

The application uses semantic search (FAISS + HuggingFace embeddings) to find the most relevant chunks of your PDF, then passes them to the Groq LLM to generate a grounded answer.

---

## ✨ Features

- 📄 **PDF Upload** — upload any PDF via a clean HTML UI
- 🔍 **Semantic Search** — FAISS vector store with HuggingFace sentence-transformers
- 🧠 **LLM-powered Q&A** — uses Groq's fast inference API (LLaMA / Mixtral)
- ⚡ **FastAPI backend** — async, production-grade REST API
- 🐳 **Docker support** — containerized for easy deployment
- 🤗 **HuggingFace Spaces** — deployed and publicly accessible

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Backend | FastAPI (Python 3.11) |
| LLM | Groq API (LLaMA 3 / Mixtral) |
| Embeddings | HuggingFace `sentence-transformers` |
| Vector Store | FAISS |
| RAG Framework | LangChain |
| Frontend | HTML + CSS + JS (vanilla) |
| Containerization | Docker |
| Hosting | HuggingFace Spaces |

---

## 🚀 Getting Started

### Prerequisites

- Python 3.11+
- A [Groq API key](https://console.groq.com/) (free tier available)

### 1. Clone the repository

```bash
git clone https://github.com/vishnureddy1210/rag-chatbot-fastapi.git
cd rag-chatbot-fastapi
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Set your API key

```bash
export GROQ_API_KEY=your_groq_api_key_here
```

### 4. Run the app

```bash
uvicorn main:app --reload
```

Open your browser at `http://localhost:8000`.

---

## 🐳 Running with Docker

```bash
docker build -t rag-chatbot .
docker run -p 7860:7860 -e GROQ_API_KEY=your_key_here rag-chatbot
```

---

## 🗂️ Project Structure

```
├── main.py              # FastAPI app — routes and server logic
├── rag_engine.py        # Core RAG pipeline (embeddings, FAISS, LLM chain)
├── templates/           # HTML UI templates
├── requirements.txt     # Python dependencies
├── Dockerfile           # Container config (HuggingFace Spaces compatible)
├── fix.py               # Utility: pin Python 3.11 + sentence-transformers fix
├── fix_rag.py           # Utility: restore HuggingFaceEmbeddings in rag_engine
└── .python-version      # Pinned to Python 3.11
```

---

## ⚙️ How It Works

```
User uploads PDF
       ↓
PDF is split into text chunks (LangChain TextSplitter)
       ↓
Each chunk is embedded using HuggingFace sentence-transformers
       ↓
Embeddings are indexed in a FAISS vector store
       ↓
User asks a question
       ↓
Question is embedded → top-k relevant chunks retrieved via FAISS
       ↓
Chunks + question sent to Groq LLM
       ↓
Answer returned to user
```

---

## 🌐 Live Demo

Try it here 👉 [https://huggingface.co/spaces/vishnuvardhanreddy12/rag-chatbot-fastapi](https://huggingface.co/spaces/vishnuvardhanreddy12/rag-chatbot-fastapi)

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to open an issue or submit a pull request.

---

## 📜 License

This project is open source. See the repository for license details.

---

## 👤 Author

**Vishnu Vardhan Reddy**  
[GitHub](https://github.com/vishnureddy1210) · [HuggingFace](https://huggingface.co/vishnuvardhanreddy12)
