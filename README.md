# PDF RAG Question Answering System

A Retrieval-Augmented Generation (RAG) based Question Answering system that allows users to upload a PDF document and ask questions about its contents.

The system retrieves relevant information from the document using semantic search and generates answers using a local instruction-tuned language model.

## 🚀 Features

- Upload and process PDF documents
- Extract text from PDF pages
- Split documents into overlapping chunks
- Generate semantic embeddings
- Store document embeddings in ChromaDB
- Perform similarity-based document retrieval
- Generate contextual answers using Qwen
- Display source page numbers
- Prevent answers from using information outside the provided context

## 🧠 Architecture

PDF Document
      ↓
Text Extraction
      ↓
Document Chunking
      ↓
BGE Embeddings
      ↓
ChromaDB Vector Store
      ↓
Semantic Retrieval
      ↓
Relevant Context
      ↓
Qwen 2.5 1.5B Instruct
      ↓
Generated Answer
      ↓
Source Pages

## 🛠️ Technologies Used

- Python
- Google Colab
- PyPDF
- Sentence Transformers
- BAAI/bge-small-en-v1.5
- ChromaDB
- Hugging Face Transformers
- Qwen/Qwen2.5-1.5B-Instruct
- Accelerate

## 🔍 How It Works

### 1. PDF Processing

The system reads the uploaded PDF using PyPDF and extracts text from each page.

### 2. Chunking

The extracted text is divided into smaller chunks of approximately 1000 characters with an overlap of 200 characters.

### 3. Embedding Generation

Each chunk is converted into a vector representation using:

`BAAI/bge-small-en-v1.5`

### 4. Vector Storage

The embeddings are stored in a ChromaDB collection.

### 5. Retrieval

When the user asks a question, the question is converted into an embedding and compared against the stored document embeddings.

The most relevant chunks are retrieved.

### 6. Answer Generation

The retrieved chunks are passed as context to:

`Qwen/Qwen2.5-1.5B-Instruct`

The model is instructed to answer only using the provided document context.

### 7. Source Tracking

The system also returns the page numbers from which the retrieved information was obtained.

## 💻 Example

Question:

> What is the hostel fee?

The system retrieves the most relevant PDF sections and provides the answer based on the document.

## ▶️ Running the Project

This project is designed to run in Google Colab.

### Install dependencies

```bash
pip install -q transformers sentence-transformers chromadb pypdf accelerate# PDF RAG QA System

This is a Python project for PDF-based RAG (Retrieval-Augmented Generation) Q&A system.

## Files
- untitled13.py: Main project file
