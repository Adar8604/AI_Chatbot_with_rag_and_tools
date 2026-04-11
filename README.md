# AI Chatbot with RAG, Tools, and Chat History

A Streamlit-based AI chatbot built with LangGraph, LangChain, FAISS, and Groq.  
It supports:
- direct LLM responses
- PDF-based RAG for document Q&A
- stock price lookup
- calculator tool
- DuckDuckGo web search
- threaded chat history with persistent checkpointing

## Features

- **PDF RAG**: Upload a PDF and ask questions about its content.
- **Tool calling**: The assistant can use:
  - `rag_tool` for document retrieval
  - `calculator` for arithmetic
  - `get_stock_price` for live stock data
  - `DuckDuckGoSearchRun` for search
- **Conversation memory**: Chat history is stored using LangGraph checkpointing with SQLite.
- **Multi-chat support**: Start a new chat and revisit previous conversations.
- **Streamlit UI**: Simple sidebar for uploads and chat switching.

## Project Files

This project is centered around two Python files:

- `chatbot_rag_backend.py` — LangGraph workflow, tools, PDF ingestion, retriever storage, and checkpoint setup. fileciteturn0file0
- `chatbot_rag_frontend.py` — Streamlit UI, chat input/output, PDF upload, conversation switching, and session state handling. fileciteturn0file1

## Suggested Folder Structure

```text
chatbot-rag-project/
├── chatbot_rag_backend.py
├── chatbot_rag_frontend.py
├── requirements.txt
├── README.md
├── .env
├── ai_chatbot.db
├── .gitignore
└── assets/
```

A cleaner long-term structure could be:

```text
chatbot-rag-project/
├── app/
│   ├── backend.py
│   └── frontend.py
├── data/
│   └── uploads/
├── assets/
├── .env
├── requirements.txt
├── README.md
├── .gitignore
└── ai_chatbot.db
```

## Setup

### 1) Create a virtual environment

```bash
python -m venv venv
```

Activate it:

```bash
# macOS / Linux
source venv/bin/activate

# Windows
venv\Scripts\activate
```

### 2) Install dependencies

```bash
pip install -r requirements.txt
```

### 3) Add environment variables

Create a `.env` file in the project root:

```env
GROQ_API_KEY=your_groq_api_key
```

Your current backend also calls Alpha Vantage directly for stock prices. The API key is hardcoded in the script right now, so it is better to move it to an environment variable before pushing to GitHub.

Recommended:

```env
ALPHA_VANTAGE_API_KEY=your_alpha_vantage_key
```

## Run the app

If your frontend file is named `chatbot_rag_frontend.py`:

```bash
streamlit run chatbot_rag_frontend.py
```

## How it works

1. The frontend creates a chat thread and keeps UI state in Streamlit.
2. When you upload a PDF, the backend:
   - loads the PDF with `PyPDFLoader`
   - splits it into chunks
   - creates a FAISS vector store
   - stores the retriever per thread
3. The LangGraph agent uses tools when needed.
4. Responses and tool calls are checkpointed in SQLite, so conversations can be revisited later.

## Notes

- Make sure Ollama is running locally if you are using `OllamaEmbeddings(model="nomic-embed-text")`.
- Make sure the required model is available in your local Ollama setup.
- The current code uses a local SQLite database named `ai_chatbot.db`.

## Recommended Improvements Before Publishing

- Move API keys out of source code and into `.env`
- Add `.gitignore` to exclude:
  - `.env`
  - `ai_chatbot.db`
  - `__pycache__/`
  - `.streamlit/`
  - `.venv/` or `venv/`
- Split backend and frontend into an `app/` folder if you want a more professional repo structure

## License

Add a license before sharing publicly on GitHub.
