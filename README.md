# 🧠 Overview of Document QA Pipeline using OpenAI + ChromaDB

This script builds an end-to-end **Question Answering (QA) System** using:

- **OpenAI** for generating text embeddings and answers
- **ChromaDB** for storing and retrieving document chunks via vector similarity

---

## 📂 Folder Structure

```
project-root/
├── .env                       # Contains OPENAI_API_KEY
├── main.py                   # Your main script
├── news_articles/            # Folder with text files to index
└── chroma_persistent_storage/  # ChromaDB local storage
```

---

## 🛠️ Key Steps

### 1. **Load Environment Variables**
Uses `dotenv` to securely load your OpenAI API key from `.env` file.

### 2. **Set up ChromaDB Collection**
Initializes a persistent collection with OpenAI embeddings.

### 3. **Load Documents**
Reads all `.txt` files from the `news_articles/` folder.

### 4. **Split Documents into Chunks**
Breaks each document into overlapping chunks (default 1000 chars with 20-char overlap) to ensure context continuity.

### 5. **Generate Embeddings with OpenAI**
Uses OpenAI’s `text-embedding-3-small` model to convert each chunk into a high-dimensional vector.

### 6. **Store Embeddings in ChromaDB**
Upserts document chunks and their embeddings into ChromaDB for fast semantic search.

### 7. **Query Documents by Question**
Given a user question, retrieves the top matching chunks from the vector database.

### 8. **Generate Final Answer**
Combines the retrieved chunks into a prompt and sends it to OpenAI’s `gpt-3.5-turbo` model to generate a concise answer.

---

## 🧪 Example Query

```python
question = "tell me about databricks"
relevant_chunks = query_documents(question)
answer = generate_response(question, relevant_chunks)
print(answer)
```

---

## ✅ Use Cases

- Internal Knowledge Base
- Document Summarization
- Legal or Research Paper QA
- Helpdesk Automation

---

## 🔒 Security Tip

Never commit your `.env` file to version control!

---

## 📌 Summary

This pipeline enables **semantic search** + **natural language answering** from your custom documents with the power of LLMs. It's modular, customizable, and a strong foundation for any AI-powered assistant.
