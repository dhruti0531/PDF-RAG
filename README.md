# 📄 PDF-RAG: Retrieval-Augmented Generation for Intelligent Document Question Answering

## Overview

PDF-RAG is an AI-powered document intelligence system that enables users to interact with PDF documents using natural language queries. The application leverages Retrieval-Augmented Generation (RAG) to retrieve relevant information from PDF files and generate accurate, context-aware responses using a Large Language Model (LLM).

Traditional document search methods rely heavily on keyword matching, often failing to capture the semantic meaning behind user queries. PDF-RAG addresses this challenge by combining semantic embeddings, vector databases, and generative AI to provide precise answers grounded in the content of the uploaded document.

The system extracts textual content from PDF files, performs document analysis, generates vector embeddings using Google's EmbeddingGemma model, stores embeddings in ChromaDB, and retrieves the most relevant context through similarity search. The retrieved context is then passed to a Groq-hosted LLM, ensuring that generated responses remain relevant to the source document.

---

## Problem Statement

Organizations, researchers, students, and professionals frequently work with large PDF documents containing valuable information. Manually searching through lengthy documents is time-consuming and inefficient. Traditional search systems often struggle to understand contextual meaning, leading to inaccurate or incomplete results.

The objective of this project is to develop an intelligent document question-answering system capable of understanding document content semantically and providing accurate responses based solely on information present within the uploaded PDF.

---

## Key Features

### Document Processing

* Upload and process PDF documents
* Automatic text extraction using PyPDFLoader
* Document content cleaning and preprocessing

### Exploratory Data Analysis (EDA)

* Total Pages
* Word Count
* Character Count
* Chunk Statistics
* Average Chunk Size Analysis

### Semantic Search

* Context-aware retrieval
* Vector similarity search
* Embedding-based document understanding

### Retrieval-Augmented Generation

* Relevant context retrieval from PDF
* Context-grounded answer generation
* Reduced hallucinations

### Interactive User Interface

* Built using Streamlit
* PDF upload through sidebar
* Question-answer interface
* Retrieved context visualization

---

## System Architecture

```text
                    ┌─────────────────┐
                    │      User       │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │   Upload PDF    │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │  PyPDFLoader    │
                    │ Text Extraction │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │   PDF Analysis  │
                    │      (EDA)      │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │  Text Chunking  │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │ EmbeddingGemma  │
                    │ Vector Creation │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │    ChromaDB     │
                    │ Vector Storage  │
                    └────────┬────────┘
                             │
               User Query    │
                    │        │
                    ▼        ▼
                    ┌─────────────────┐
                    │ Similarity      │
                    │ Retrieval       │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │  Relevant       │
                    │  Context        │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │    Groq LLM     │
                    │  Answer Engine  │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │ Generated Answer│
                    └─────────────────┘
```

---

## Technology Stack

| Category               | Technology                 |
| ---------------------- | -------------------------- |
| Programming Language   | Python                     |
| Frontend Framework     | Streamlit                  |
| AI Framework           | LangChain                  |
| Embedding Model        | EmbeddingGemma-300M        |
| Vector Database        | ChromaDB                   |
| Large Language Model   | Llama 3.1 via Groq         |
| PDF Processing         | PyPDFLoader                |
| Environment Management | Python Virtual Environment |
| Version Control        | Git & GitHub               |

---

## Project Structure

```text
PDF-RAG/
│
├── app.py
├── vector.py
├── vector_search.py
├── requirements.txt
├── README.md
├── .env
├── .gitignore
│
├── uploads/
│
├── chroma_langchain_db/
│
└── __pycache__/
```

---

## Installation

### 1. Clone Repository

```bash
git clone <repository-url>
cd PDF-RAG
```

### 2. Create Virtual Environment

```bash
python -m venv venv
```

### 3. Activate Virtual Environment

#### Windows

```bash
venv\Scripts\activate
```

#### Linux / macOS

```bash
source venv/bin/activate
```

### 4. Install Dependencies

```bash
pip install -r requirements.txt
```

---

## Environment Configuration

Create a `.env` file in the project root directory:

```env
GROQ_API_KEY=your_groq_api_key
```

---

## Running the Application

### Generate Vector Database

```bash
python vector.py
```

This step performs:

* PDF Loading
* Text Extraction
* Text Chunking
* Embedding Generation
* ChromaDB Vector Database Creation

### Launch Streamlit Application

```bash
streamlit run app.py
```

The application will open automatically in your browser.

---

## Application Workflow

### Step 1: Upload PDF

The user uploads a PDF document through the Streamlit sidebar.

### Step 2: Document Processing

The uploaded document is processed using PyPDFLoader to extract textual content.

### Step 3: Exploratory Data Analysis

The system displays document insights including:

* Total Pages
* Total Words
* Character Count
* Number of Chunks
* Chunk Statistics

### Step 4: Embedding Generation

The extracted text is divided into overlapping chunks and converted into vector embeddings using:

```text
google/embeddinggemma-300m
```

### Step 5: Vector Storage

Generated embeddings are stored in ChromaDB for efficient semantic retrieval.

### Step 6: User Query Processing

When a question is submitted:

1. Query embedding is generated.
2. Similarity search is performed.
3. Relevant document chunks are retrieved.

### Step 7: Answer Generation

Retrieved context is combined with the user query and sent to the Groq-hosted LLM for answer generation.

### Step 8: Response Display

The generated answer and retrieved context are displayed through the Streamlit interface.

---

## Advantages

* Intelligent PDF Question Answering
* Semantic Search Capabilities
* Context-Aware Responses
* Reduced Hallucinations
* Fast Retrieval using Vector Databases
* User-Friendly Interface
* Scalable Architecture
* Efficient Document Understanding
* Improved Information Accessibility
* Easy Integration with Additional LLMs

---

## Applications

* Academic Research Assistance
* Research Paper Analysis
* Technical Documentation Search
* Cybersecurity Knowledge Retrieval
* Enterprise Knowledge Management
* Legal Document Exploration
* Educational Learning Platforms
* Report Analysis and Information Extraction

---

## Future Enhancements

* Multi-PDF Question Answering
* Conversational Memory
* PDF Summarization
* Support for DOCX, TXT, and PPT Files
* Cloud Deployment
* User Authentication
* Role-Based Access Control
* Multilingual Support
* Image and Table Understanding
* Advanced Analytics Dashboard

---

## Results

The developed system successfully demonstrates the practical implementation of Retrieval-Augmented Generation for document intelligence. Experimental testing shows efficient document processing, accurate semantic retrieval, and context-aware answer generation. The integration of EmbeddingGemma, ChromaDB, LangChain, and Groq provides a robust framework for intelligent document interaction.
