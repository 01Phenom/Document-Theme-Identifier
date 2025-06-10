# 📄 Document Research & Theme Identification System

This project is a document research and theme identification system that allows users to upload PDF documents, query their content, and discover thematic connections across documents. The system uses AI to extract information from documents and identify common themes.

---

## 🚀 Features

- **Document Upload**: Upload and process PDF documents
- **Document Management**: View, filter, and delete documents
- **Semantic Search**: Query documents using natural language
- **Theme Identification**: Automatically identify themes across documents
- **Direct Answers**: Get concise answers to specific questions

---

## 🏗 Project Structure

- **Backend**: FastAPI application with modular services
- **Frontend**: Streamlit web interface
- **Vector Database**: ChromaDB for document embeddings and semantic search
- **LLM Integration**: Google Generative AI for text processing and theme identification

---

## ⚙️ Prerequisites

- Python 3.8+
- Google API Key for Generative AI services

---

## 🧪 Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/01Phenom/Document-Theme-Identifier.git
   cd wasserstoff-AiInternTask
   ```

2. Create and activate a virtual environment:
   ```bash
   python -m venv wasserstoff
   .\wasserstoff\Scripts\activate
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Set up environment variables:
   - Create a `.env` file in the root directory and add:
     ```
     GOOGLE_API_KEY=your_api_key_here
     ```
   - Or temporarily in PowerShell:
     ```bash
     $env:GOOGLE_API_KEY="YOUR_KEY_HERE"
     ```

---

## ▶️ Running the Application

### 🔧 Backend

Start the FastAPI backend:
```bash
cd backend
uvicorn app.main:app --reload
```
- API Base URL: [http://localhost:8000](http://localhost:8000)
- Swagger Docs: [http://localhost:8000/docs](http://localhost:8000/docs)

### 🎛 Frontend

Launch the Streamlit interface:
```bash
cd demo
streamlit run app.py
```
- App UI: [http://localhost:8501](http://localhost:8501)

> 💡 **Note**: Hosting is best done locally or on paid cloud platforms due to file storage requirements.

---

## 🧠 Usage Guide

1. Open [http://localhost:8501](http://localhost:8501) in your browser.
2. Upload PDF files via the sidebar.
3. Wait for processing to complete.
4. Ask natural language questions.
5. View direct answers, identified themes, and their sources.

---

## 🔍 Solution Approach

### 📘 Document Processing Pipeline

1. **Upload** → PDFs are stored locally
2. **Text Extraction** → `pdfplumber` extracts content
3. **Chunking** → Documents are split with overlap
4. **Embedding** → Google Embedding model used
5. **Vector Storage** → Stored in ChromaDB

### ❓ Query Processing Pipeline

1. **Query Embedding** → Embedded with the same model
2. **Semantic Search** → ChromaDB returns top matches
3. **Context Building** → Relevant chunks assembled
4. **LLM Processing** → Google GenAI generates:
   - Direct answers
   - Common themes
   - Source references

### 🧵 Theme Identification

1. Analyze semantic relations across chunks
2. Use prompt engineering for clarity
3. Parse and structure LLM output
4. Display themes with citations

---

## 📡 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/api/v1/upload` | Upload a new document |
| `GET`  | `/api/v1/documents` | List all uploaded documents |
| `DELETE` | `/api/v1/delete/{doc_id}` | Delete a specific document |
| `DELETE` | `/api/v1/delete` | Delete all documents |
| `POST` | `/api/v1/query` | Submit a question/query |

---

## 🧰 Technologies Used

- [FastAPI](https://fastapi.tiangolo.com/)
- [Streamlit](https://streamlit.io/)
- [ChromaDB](https://www.trychroma.com/)
- [LangChain](https://www.langchain.com/)
- [Google Generative AI](https://ai.google.dev/)
- [PDFPlumber](https://github.com/jsvine/pdfplumber)

---

## ⚠️ Challenges Faced

| **Challenge**                    | **Impact**                                     | **Solution / Workaround**                                      |
|----------------------------------|------------------------------------------------|-----------------------------------------------------------------|
| **API rate/context limits**      | Incomplete or truncated LLM responses          | Optimized prompts, used chunk filtering, and added retry logic |
| **Large document chunking**      | Lost important context in LLM responses        | Overlapping chunk strategy and top-k semantic search           |
| **Unstructured LLM output**      | Difficulties in parsing themes and answers     | Used prompt engineering and regex-based structured parsing     |
| **Vector search inefficiency**   | Slow semantic search with large datasets       | Metadata filtering, indexing tuning, and top-k result limits   |
| **Pipeline errors**              | System breaks on failed uploads or extractions| Robust exception handling, logging, and status tracking        |
| **Scalability constraints**      | Cannot support many users or large datasets    | Recommended local use; scalable with cloud infra if needed     |
| **Hosting limitations**          | Loss of uploaded files on free-tier platforms  | Local deployment or cloud services with persistent storage     |
| **Poor user experience (UX)**    | Users unsure if system is working or stuck     | UI status updates, progress indicators, and source citations   |

---

## 🧑‍💻 Author

- [@01Phenom](https://github.com/01Phenom)

---

Feel free to fork, use, or extend this project. Contributions and suggestions are welcome!
