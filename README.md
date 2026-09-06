# AG's GPT

AG's GPT is an agentic AI chatbot that combines Large Language Models with tool calling, web search, document-based Retrieval-Augmented Generation (RAG), and persistent conversation memory.

The application provides a web-based chat interface where users can interact with an AI assistant, search for current information, upload documents, and ask questions based on those documents.

> Built and customized by AG.

---

## 🚀 Features

- 💬 AI-powered conversational chatbot
- 🤖 Agentic workflow using LangGraph
- 🔧 Tool calling and tool execution
- 🌐 Web search using Tavily
- 📄 Document upload and question answering
- 🧠 Retrieval-Augmented Generation (RAG)
- 🔍 Semantic search using ChromaDB
- 💾 Persistent conversation memory
- ⚡ Real-time streaming responses
- 🎨 Custom black-and-white user interface
- 🗂️ Conversation history

---

# 🏗️ Architecture

```text
                    USER
                      │
                      ▼
                 AG's GPT UI
                      │
                      ▼
                   FastAPI
                      │
                      ▼
                LangGraph Agent
                      │
          ┌───────────┼───────────┐
          │           │           │
          ▼           ▼           ▼
        Gemini      Tavily        RAG
         LLM       Web Search     │
                                  ▼
                              ChromaDB
                                  │
                                  ▼
                           Relevant Context
                                  │
                                  ▼
                          Final AI Response
                                  │
                                  ▼
                                 USER
```

---

# 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| FastAPI | Backend and API |
| LangGraph | Agent workflow orchestration |
| LangChain | LLM and tool integration |
| Google Gemini | Large Language Model |
| Tavily | Web search |
| ChromaDB | Vector database |
| SQLite | Persistent data storage |
| HTML / CSS / JavaScript | Frontend |
| Uvicorn | ASGI server |

---

# 🤖 Agent Workflow

AG's GPT uses a tool-based agent workflow.

Instead of directly sending every user message to the LLM and returning a response, the agent can decide whether additional tools are required.

```text
User Message
     │
     ▼
    LLM
     │
     ▼
tools_condition
     │
 ┌───┴────┐
 │        │
No Tool   Tool Required
 │        │
 ▼        ▼
Answer   ToolNode
             │
             ▼
        Execute Tool
             │
             ▼
       Return Result
             │
             ▼
            LLM
             │
             ▼
       Final Response
```

### `tools_condition`

Checks whether the LLM has requested a tool.

### `ToolNode`

Executes the requested tool and returns the result to the agent workflow.

---

# 🌐 Web Search

AG's GPT can use Tavily to retrieve current information from the web.

```text
User Question
      │
      ▼
LangGraph Agent
      │
      ▼
Current Information Needed?
      │
      ▼
Tavily Web Search
      │
      ▼
Search Results
      │
      ▼
LLM
      │
      ▼
Final Response
```

---

# 📄 Document-Based RAG

Users can upload supported documents and ask questions based on their content.

```text
Document Upload
       │
       ▼
Text Extraction
       │
       ▼
Text Chunking
       │
       ▼
Embedding Generation
       │
       ▼
ChromaDB
```

When a user asks a question:

```text
User Question
       │
       ▼
Retrieve Relevant Document Chunks
       │
       ▼
Provide Context to LLM
       │
       ▼
Generate Answer
```

This allows AG's GPT to answer questions based on uploaded documents instead of relying only on the LLM's general knowledge.

---

# 🧠 Persistent Memory

AG's GPT includes persistent conversation memory.

The application can store and retrieve relevant information from previous interactions, helping the chatbot maintain context instead of treating every conversation as completely independent.

```text
Conversation
     │
     ▼
Persistent Storage
     │
     ▼
Stored Context
     │
     ▼
Future Interactions
```

---

# 📁 Project Structure

```text
AGs-GPT/
│
├── app.py                  # FastAPI application and API endpoints
├── agent.py                # LangGraph agent and workflow
├── database.py             # Conversation and persistent storage logic
├── rag.py                  # RAG and document retrieval pipeline
├── tools.py                # Agent tools
│
├── templates/
│   └── index.html          # Frontend user interface
│
├── uploads/                # Uploaded documents
├── data/                   # Application data and persistent storage
├── chroma_db/              # ChromaDB vector database
│
├── requirements.txt        # Python dependencies
├── pyproject.toml          # Project configuration
└── README.md
```

---

# ⚙️ Installation

## 1. Clone the Repository

```bash
git clone <your-repository-url>
cd AGs-GPT
```

## 2. Create a Virtual Environment

This project uses Python 3.11.

Using `uv`:

```bash
uv venv --python 3.11
```

Activate the environment on Windows:

```powershell
.venv\Scripts\activate
```

## 3. Install Dependencies

Using `uv`:

```bash
uv add -r requirements.txt
```

Alternatively, using pip:

```bash
pip install -r requirements.txt
```

---

# 🔑 Environment Variables

Create a `.env` file in the project root:

```env
GOOGLE_API_KEY=your_google_api_key

GOOGLE_MODEL=your_gemini_model

TAVILY_API_KEY=your_tavily_api_key

LANGSMITH_TRACING=false
LANGSMITH_ENDPOINT=https://api.smith.langchain.com
LANGSMITH_API_KEY=your_langsmith_api_key
LANGSMITH_PROJECT=ags-gpt
```

> Do not commit your `.env` file to GitHub.

---

# ▶️ Run the Application

```bash
python app.py
```

The application will run locally at:

```text
http://127.0.0.1:8080
```

---

# 💡 Example Use Cases

### General AI Chat

```text
Explain how LangGraph ToolNode works.
```

### Web Search

```text
What are the latest developments in AI?
```

### Document Question Answering

Upload a PDF and ask:

```text
Summarize the key findings of this document.
```

---

# 🎨 User Interface

AG's GPT features a custom minimal black-and-white user interface with:

- Chat interface
- Model selection
- File uploads
- Conversation history
- Real-time response streaming

---

# 🔮 Future Improvements

- Multi-agent architecture
- Voice output
- Improved long-term memory
- User authentication
- Conversation export
- Advanced document management
- Docker deployment
- Automated testing
- CI/CD pipeline
- Cloud deployment

---

#  Author

**AG**

AG's GPT is a customized and extended agentic AI chatbot project focused on understanding and building practical AI agent workflows.

---

# ⚠️ Disclaimer

AG's GPT can make mistakes. Always verify important information.
