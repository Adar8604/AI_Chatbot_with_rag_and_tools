# 🤖 AI Chatbot with RAG, Tools & Streaming UI

An AI-powered chatbot built using LangGraph and LangChain that supports real-time conversations, PDF-based retrieval (RAG), and tool integration (calculator, stock data, and web search). It features a Streamlit interface with streaming responses and persistent chat history.

---

## 🚀 Features

* 💬 LLM-powered chatbot (Groq + Llama 3)
* 📄 RAG over PDFs (FAISS + embeddings)
* 🛠️ Tool integration:

  * Calculator
  * Stock price API
  * Web search (DuckDuckGo)
* ⚡ Real-time streaming responses
* 🧠 Multi-session chat with memory (thread-based)
* 🎯 Clean and interactive Streamlit UI

---

## 🏗️ Tech Stack

* **LLM & Agents**: LangChain, LangGraph
* **Model Provider**: Groq (Llama 3)
* **Vector Store**: FAISS
* **Embeddings**: Ollama
* **Frontend**: Streamlit
* **Backend**: Python
* **Database**: SQLite (for chat memory)

---

## 📂 Project Structure

```
AI_CHATBOT/
├── chatbot_backend.py
├── chatbot_frontend.py
├── requirements.txt
├── README.md
├── .gitignore
└── .env
```

---

## ⚙️ Setup Instructions

### 1️⃣ Clone the repository

```
git clone https://github.com/<your-username>/ai-chatbot-rag.git
cd ai-chatbot-rag
```

---

### 2️⃣ Create environment (recommended)

Using conda:

```
conda create -n chatbot python=3.10 -y
conda activate chatbot
```

---

### 3️⃣ Install dependencies

```
pip install -r requirements.txt
```

---

### 4️⃣ Add environment variables

Create a `.env` file:

```
GROQ_API_KEY=your_groq_api_key
ALPHA_VANTAGE_API_KEY=your_alpha_vantage_key
```

---

### 5️⃣ Run the app

```
streamlit run chatbot_frontend.py
```

---

## 🧠 How It Works

1. User inputs a query via Streamlit UI
2. LangGraph agent decides:

   * Direct LLM response OR
   * Tool usage OR
   * RAG retrieval from uploaded PDF
3. If PDF is uploaded:

   * Text is chunked and stored in FAISS
   * Relevant chunks are retrieved for answers
4. Responses are streamed live to the UI
5. Chat history is maintained using thread-based memory

---

## 📸 Demo (Optional)

*Add screenshots here to make your project stand out*

---

## 💡 Future Improvements

* 🔐 Authentication & user accounts
* ☁️ Deployment (AWS / Render / GCP)
* 📊 Observability with LangSmith
* 🧾 Support for multiple file formats
* ⚡ Faster retrieval with hybrid search

---

## 🏆 Resume Highlight

> Developed an AI chatbot with RAG-based document retrieval and tool integration using LangGraph and LangChain, supporting real-time streaming responses and multi-session chat.

---

## 📜 License

This project is open-source and available under the MIT License.

---

## 🙌 Acknowledgements

* LangChain & LangGraph
* Groq API
* Streamlit
* FAISS

---
