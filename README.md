# AI Homelab Platform

A modular local AI orchestration platform built using Docker Compose, n8n, Ollama, Docling, and Qdrant.

This project provides a scalable foundation for:
- AI workflows
- document processing
- local LLM inference
- RAG (Retrieval Augmented Generation)
- automation pipelines
- AI agents

---

## 🚀 Features

- Modular Docker Compose architecture
- Local LLM inference using Ollama
- Document parsing and OCR using Docling
- Workflow orchestration using n8n
- Vector database using Qdrant
- Static file hosting using Nginx
- Shared inter-service storage
- GPU acceleration support (NVIDIA)

---

## 🏗️ Architecture

```text
Client/API
    ↓
n8n (Workflow Orchestrator)
    ↓
 ┌───────────────┬───────────────┐
 ↓               ↓               ↓
Docling       Ollama         Qdrant
(Document)    (LLM)          (Vectors)
```
---

## 📁 Directory Structure

```text
ai/
│
├── .env
│
├── core/
│   └── docker-compose.yml
│
├── orchestrator/
│   └── docker-compose.yml
│
├── ai-services/
│   └── docker-compose.yml
│
├── extensions/
│   └── docker-compose.yml
│
├── shared/
│   ├── extracted-images/
│   ├── rag-files/
│   └── docling-scratch/
│
└── docker-compose.yml
└── n8n/
    └── demo-data/

```

---

## 🧱 Services

### Core Layer

| Service | Purpose |
|---|---|
| PostgreSQL | Database used by n8n |
| Qdrant | Vector database for embeddings and semantic search |

---

### Orchestrator Layer

| Service | Purpose |
|---|---|
| n8n | Workflow orchestration and automation engine |

---

### AI Services Layer

| Service | Purpose |
|---|---|
| Ollama | Local LLM inference and AI model serving |
| Docling | Document parsing, OCR, and markdown extraction |

---

### Extensions Layer

| Service | Purpose |
|---|---|
| Nginx Static Files | Serves extracted files and shared artifacts |

---

## ⚙️ Prerequisites

- Docker
- Docker Compose
- NVIDIA Container Toolkit (optional for GPU acceleration)
- Git

---

## 🔧 Environment Variables

Create a `.env` file in the project root.

Example:

```env
POSTGRES_USER=n8n
POSTGRES_PASSWORD=n8npass
POSTGRES_DB=n8n

N8N_PORT=5678
OLLAMA_PORT=11434
DOCLING_PORT=5001

N8N_ENCRYPTION_KEY=your-secret-key
N8N_USER_MANAGEMENT_JWT_SECRET=your-jwt-secret
```

---

## 🚀 Running The Stack and Stopping The Stack
```code
docker compose up
docker compose down
```

---

## 🌐 Service URLs

| Service | URL |
|---|---|
| n8n | http://localhost:5678 |
| Ollama | http://localhost:11434 |
| Docling | http://localhost:5001/ui |
| Qdrant Dashboard | http://localhost:6333/dashboard |
| Static Files | http://localhost:8080 |

---

## 🤖 Example Workflow

Implemented workflow:

```text
Webhook
   ↓
Docling
   ↓
Markdown Extraction
   ↓
Ollama
   ↓
AI Summary Response
```
---

## 🧪 Example API Call and Example Response

```code
curl -X POST "http://localhost:5678/webhook/doc-summary" \
-H "Content-Type: application/json" \
-d "{}"

{
  "summary": "The paper introduces the Transformer architecture..."
}
```

---
## 🧠 Future Roadmap

- RAG (Retrieval Augmented Generation) pipeline
- Embedding generation workflows
- Semantic search using Qdrant
- AI agents and multi-agent orchestration
- Chat with PDFs and documents
- Knowledge assistant workflows
- Email and notification automation
- Monitoring and observability stack
- Web UI integration
- Advanced workflow templates

---

## 📚 Technologies Used

- Docker Compose
- n8n
- Ollama
- Docling
- Qdrant
- PostgreSQL
- Nginx
- NVIDIA Container Toolkit
- REST APIs

---

## 🎯 Goals

This project aims to provide:

- A fully local AI stack
- Modular and scalable infrastructure
- Self-hosted AI experimentation platform
- Extensible workflow orchestration
- Local-first AI processing
- AI-powered document workflows
- Foundation for RAG and AI agents
- Reusable AI automation architecture
