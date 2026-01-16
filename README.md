# Production-Style-RAG-System

This repository contains a **production-style Retrieval-Augmented Generation (RAG) system** built entirely from scratch for **student support and education knowledge retrieval**. The goal of this project is to demonstrate how reliable, domain-specific LLM systems can be designed by grounding generation in verified documents rather than relying on a model’s internal knowledge alone.

The system is implemented without frameworks such as LangChain or LlamaIndex and focuses on **transparent retrieval logic, system-level design, and output traceability**, making it suitable as a learning artifact and an AI/ML engineering portfolio project.

---

## 🚀 Project Motivation

University policies and procedures (e.g., changing majors, I-20 updates, advising rules) are often scattered across PDFs, emails, and portals. General-purpose language models tend to hallucinate or provide generic answers when asked institution-specific questions. This project addresses that problem by implementing a **retrieval-grounded QA system** that ensures all generated responses are derived directly from official documents.

---

## 🧠 System Architecture

The RAG pipeline follows a clear, modular flow:

1. **Document Ingestion & Normalization**
   Raw documents (TXT; extensible to PDF/DOCX) are loaded, cleaned, and normalized into structured text units.

2. **Chunking Strategies**
   Two chunking strategies are implemented and compared:

   * **Adaptive sentence-based chunking** to preserve procedural continuity
   * **Sliding-window chunking** to improve recall for FAQ-style content

3. **Embeddings**

   * Open-source: `all-MiniLM-L6-v2` (fast, lightweight)
   * Large-scale semantic: `E5-Large-V2` (stronger intent matching)

4. **Retrieval (From Scratch)**

   * Chunk embeddings stored in NumPy arrays
   * **Manual cosine similarity computation**
   * Top-k chunk retrieval with score transparency

5. **Grounded Generation**

   * Retrieved chunks injected into a structured prompt
   * Lightweight open-source LLM generates responses strictly from provided context

6. **Evaluation**

   * RAG vs non-RAG comparison
   * Retrieved chunk inspection and similarity score analysis

---

## 📊 Example Output

For a query like **“How do I change my major?”**, the system retrieves:

* A high-scoring procedural chunk containing the full step sequence
* Supporting contextual chunks (e.g., international student considerations)

The grounded RAG response accurately reflects official policy steps, while a non-RAG baseline produces generic or incomplete guidance. Retrieved chunks and similarity scores are surfaced alongside outputs for transparency.

---

## 🧪 Key Findings

* **Adaptive chunking** performs best for procedural documents by preserving full workflows.
* **Sliding-window chunking** improves recall for short, paraphrased FAQ-style queries.
* **E5-Large-V2 embeddings** consistently outperform MiniLM on indirect and semantic queries.
* Retrieval grounding significantly **reduces hallucinations** and improves factual correctness.

---

## 🛠 Tech Stack

* Python
* NumPy
* sentence-transformers
* transformers
* Open-source LLM (TinyLlama)

---

## 🔮 Limitations & Future Improvements

* Add robust PDF/HTML ingestion
* Introduce hybrid retrieval (BM25 + dense vectors)
* Integrate reranking with cross-encoders
* Scale retrieval using FAISS or pgvector
* Add citation formatting and metadata filtering
* Support conversational memory and user personalization

---



## 📌 Why This Repository Matters

This project demonstrates **end-to-end RAG system design**, focusing on **retrieval correctness, transparency, and system-level thinking**—core skills for modern AI/ML engineering roles.

---
