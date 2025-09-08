# 📚 Multi-PDF Chatbot using LangChain, HuggingFace & Streamlit

A conversational AI application that allows users to **chat with multiple PDF documents** at once.  
Upload research papers, reports, or books in PDF format and ask **questions in natural language**.  
The chatbot retrieves relevant text chunks from the PDFs and provides intelligent answers.

---

## 🚀 Features
- Upload **multiple PDFs** at once.
- **Text extraction** using PyPDF2.
- **Chunking** of large text into manageable pieces.
- **Vector embeddings** with `sentence-transformers/all-MiniLM-L6-v2`.
- **Semantic search** using FAISS vector database.
- **Conversational memory** to maintain chat context.
- **Generative responses** powered by Hugging Face models (`flan-t5-small`).
- **Streamlit UI** for an interactive web app.

---

## 🏗️ Architecture

1. **PDF Upload & Extraction**
   - Extracts raw text from multiple PDFs.

2. **Text Chunking**
   - Splits text into chunks (1000 chars, 200 overlap) for better retrieval.

3. **Vector Store (FAISS + HuggingFace Embeddings)**
   - Converts chunks into embeddings using **sentence-transformers/all-MiniLM-L6-v2**.
   - Stores them in a FAISS index for efficient similarity search.

4. **Conversational Retrieval Chain**
   - Uses LangChain’s `ConversationalRetrievalChain` to combine:
     - Retriever (FAISS vector DB)
     - Generator (Hugging Face LLM pipeline)
     - Memory (chat history buffer)

5. **User Interface**
   - Built with Streamlit (`streamlit run app.py`).
   - Sidebar for PDF uploads, main area for chatbot.

---

## 🧠 Why These Models?

- **HuggingFace Embeddings (`all-MiniLM-L6-v2`)**  
  - Light, fast, high-quality embeddings for semantic similarity.  
  - Converts PDF text chunks into numerical vectors for retrieval.

- **FAISS (Facebook AI Similarity Search)**  
  - Industry-standard library for efficient vector similarity search.  
  - Finds the most relevant text chunks for each user query.

- **Flan-T5 Small (via HuggingFace Pipeline)**  
  - Pre-trained, instruction-tuned model.  
  - Generates natural language answers from retrieved chunks.  
  - Chosen for being **lightweight** and easy to run locally.

- **LangChain**  
  - Provides modular abstractions to connect retrievers, LLMs, and memory.  
  - Simplifies orchestration of embeddings + FAISS + HuggingFace pipeline.

- **Streamlit**  
  - Quick, user-friendly web app for deployment.  
  - No need to build frontend from scratch.

---

## ⚙️ Installation

1. Clone the repository.
2. Install dependencies. 
```pip install -r requirements.txt```
3. Run the Streamlit app
``` streamlit run app.py ```
