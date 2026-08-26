<a name="readme-top"></a>

<div align="center">
  <h1 align="center" style="border-bottom: none">🦙 Enterprise RAG Data Framework & Document Agent Platform</h1>
  <p align="center">
    <strong>Data Framework for Retrieval-Augmented Generation (RAG), Hybrid Vector Indexing, and Autonomous Document Agents (LlamaIndex).</strong>
  </p>
</div>

<div align="center">
  <a href="https://github.com/NadeemAhmad3"><img src="https://img.shields.io/badge/Author-Nadeem%20Ahmad-blue?style=for-the-badge&logo=github" alt="Author"></a>
  <a href="mailto:engrnadeem26@gmail.com"><img src="https://img.shields.io/badge/Email-engrnadeem26%40gmail.com-red?style=for-the-badge&logo=gmail" alt="Email"></a>
  <a href="https://github.com/NadeemAhmad3/enterprise-rag-data-framework"><img src="https://img.shields.io/badge/Status-Production%20Ready-brightgreen?style=for-the-badge" alt="Status"></a>
</div>

<hr>

## 📌 Executive Overview

**Enterprise RAG Data Framework** (powered by **LlamaIndex**) is a data orchestration platform designed to augment Large Language Models (LLMs) with private enterprise data (PDFs, SQL databases, Notion, APIs, and vector databases).

It bridges raw unstructured data with foundation models by offering 300+ data connectors, vector & property graph indices, hybrid sparse/dense retrievers, cross-encoder rerankers, and event-driven document agent workflows.

```text
               ┌────────────────────────────────────────────────────────┐
               │    LLM Application / Agent Workflow Layer              │
               └───────────────────────────┬────────────────────────────┘
                                           │
         ┌─────────────────────────────────┼─────────────────────────────────┐
         ▼                                 ▼                                 ▼
┌──────────────────┐             ┌──────────────────┐             ┌──────────────────┐
│ Hybrid RAG Engine│             │ Vector & Graph   │             │ 300+ Data        │
│ (BM25 + Dense)   │             │ Indices          │             │ Connectors       │
└──────────────────┘             └──────────────────┘             └──────────────────┘
```

---

## 🔥 Core Architectural Components

### 1. 📂 Data Ingestion & Connectors (`llama-index-core`)
Incorporate unstructured data from 300+ sources (PDFs, Markdown, DOCX, PostgreSQL, Notion, Slack) using `SimpleDirectoryReader` and LlamaHub connectors.

### 2. 🗂️ Advanced Indexing & Knowledge Graphs
- **VectorStoreIndex**: Dense vector embeddings integrated with Qdrant, Pinecone, Chroma, and Milvus.
- **PropertyGraphIndex**: Construct Knowledge Graphs connecting entities and concepts across complex documents.
- **Summary & Tree Indices**: Hierarchical document summarization trees.

### 3. 🔍 Hybrid Retrieval & Reranking (`RetrieverQueryEngine`)
- **Hybrid Search**: Fuses sparse BM25 keyword matching with dense vector similarity search.
- **Cross-Encoder Reranking**: Re-ranks top-K retrieved context chunks using Cohere or BGE rerankers to eliminate RAG hallucinations.

### 4. 🤖 Stateful Document Agent Workflows (`llama-index-core/workflow`)
Event-driven multi-step agent workflows that decompose complex analytical questions into sub-queries across multiple documents.

---

## 📂 Repository Architecture

```text
enterprise-rag-data-framework/
├── llama-index-core/              # Core Engine: Indexing, Retrievers, QueryEngines, Workflows
│   ├── llama_index/core/
│   │   ├── indices/               # Vector, Graph, and Summary index structures
│   │   ├── retrievers/            # Vector, BM25, and Hybrid retrievers
│   │   ├── query_engine/          # RAG query engines & response synthesizers
│   │   ├── postprocessor/         # Rerankers (Cohere, SentenceTransformerRerank)
│   │   └── workflow/              # Event-driven RAG agent workflows
├── llama-index-integrations/      # 300+ Provider Integrations (OpenAI, Qdrant, Pinecone, Cohere)
├── llama-index-instrumentation/   # Built-in OpenTelemetry & observability instrumentation
└── docs/                          # Framework & LlamaParse documentation
```

---

## ⚡ Quickstart Guide

### 1. Installation

```bash
pip install llama-index
```

### 2. Basic RAG Pipeline Example

```python
import os
from llama_index.core import VectorStoreIndex, SimpleDirectoryReader

# Set OpenAI API Key
os.environ["OPENAI_API_KEY"] = "YOUR_OPENAI_API_KEY"

# 1. Load Local Documents
documents = SimpleDirectoryReader("data").load_data()

# 2. Build Vector Index
index = VectorStoreIndex.from_documents(documents)

# 3. Create Query Engine & Query
query_engine = index.as_query_engine()
response = query_engine.query("What are the key insights in this document?")
print(response)
```

---

## 👤 Maintainer & Author Information

* **Author**: **Nadeem Ahmad**
* **GitHub**: [@NadeemAhmad3](https://github.com/NadeemAhmad3)
* **Email**: [engrnadeem26@gmail.com](mailto:engrnadeem26@gmail.com)
* **Repository**: [https://github.com/NadeemAhmad3/enterprise-rag-data-framework](https://github.com/NadeemAhmad3/enterprise-rag-data-framework)

---

## 📄 License

Distributed under the MIT License. See [`LICENSE`](./LICENSE) for full details.
