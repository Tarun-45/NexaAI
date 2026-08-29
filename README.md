# NexaDoc AI - Multimodal Document Intelligence & RAG Platform

NexaDoc AI is a multimodal Retrieval-Augmented Generation (RAG) system that allows users to ask questions about complex PDF documents containing text, tables, charts, figures, and diagrams.

Unlike traditional document chatbots that primarily process text, NexaDoc AI combines document parsing, semantic retrieval, keyword search, and vision-based analysis to retrieve relevant information from both textual and visual content.

The system is designed for research papers, financial reports, technical documents, and other information-dense PDFs where important insights may exist inside tables, charts, and figures.

---

## 🎯 Problem Statement

Traditional PDF question-answering systems mainly focus on extracting and searching text. This can cause important information inside tables, graphs, charts, and figures to be missed.

For example, a user may ask:

> "What does Figure 8 show about LNG supply?"

A text-only RAG system may fail to answer this question accurately because the required information may exist inside a visual figure rather than plain text.

NexaDoc AI addresses this problem by building a multimodal document intelligence pipeline capable of processing:

- Text
- Tables
- Charts
- Figures
- Diagrams

The system retrieves relevant information from the document and uses language and vision models to generate a contextual answer.

---

## 🚀 Key Features

### 1. Multimodal Document Ingestion

NexaDoc AI processes different types of content present inside PDF documents instead of relying only on extracted text.

The system handles:

- Text
- Tables
- Charts
- Figures
- Diagrams

Visual content is extracted and analyzed using Gemini Vision.

---

### 2. Intelligent Table Extraction

Tables are extracted using LlamaParse in Markdown format while preserving their structural relationships as much as possible.

This helps the retrieval system understand relationships between:

- Rows
- Columns
- Headers
- Values

This is particularly useful for questions involving numerical data and structured information.

---

### 3. Hybrid Retrieval

NexaDoc AI combines two complementary retrieval techniques:

**Semantic Search**

Uses FAISS to retrieve information based on semantic similarity and meaning.

**Keyword Search**

Uses BM25 to retrieve information based on exact keywords, technical terms, names, and numerical values.

The results from both retrieval approaches are combined to improve document retrieval.

```text
User Question
      ↓
 ┌───────────────┐
 │ Query         │
 └───────┬───────┘
         ↓
 ┌───────────────────────┐
 │ Hybrid Retrieval      │
 │                       │
 │ FAISS + BM25          │
 └───────────┬───────────┘
             ↓
      Relevant Context
             ↓
      LLM / Vision Model
             ↓
          Answer
