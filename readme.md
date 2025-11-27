
# Conversational Knowledge Bot  
**LangChain + Gemini 2.0 Flash + Tools + Memory + Streamlit UI**

The Conversational Knowledge Bot intelligently answers questions using live web search + LLM reasoning, while remembering previous context.  
Designed for **Task 2: Conversational Knowledge Bot** — fully compliant.



## Features

### Conversational Memory  
Remembers multi‑turn conversations via `ConversationBufferMemory(return_messages=True)`.

### Real‑Time Search (DuckDuckGo)  
No API key needed. (`ddgs`‑based search tool)  
 *app/tools/web_search.py*

### Gemini 2.0 Flash LLM  
Custom‑wrapped model for LangChain reasoning + inference.  
 *app/models/gemini_llm.py*

### ReAct Agent with Tools + Memory  
LLM selects tools and generates deep contextual responses.  
 *app/agent.py*

### Streamlit UI  
Fully interactive chatbot interface with persistent memory.  
 *app/main.py*

Run:
```
streamlit run app/main.py
```



## Architecture

```
 UI (Streamlit Chat)
          │
          ▼
   LangChain Agent
          │
 ┌────────┼─────────┐
 ▼        ▼         ▼
Memory  Web‑Search  Gemini Flash
```


##  Repo Structure

```
conversational-bot/
│
├── app/
│   ├── main.py
│   ├── agent.py
│   ├── memory_store.py
│   ├── models/
│   │   └── gemini_llm.py
│   └── tools/
│       └── web_search.py
│
├── requirements.txt
├── .env
└── README.md
```



##  Setup

```bash
git clone https://github.com/jbittu/conversational_bot.git
cd conversational_bot
python -m venv venv      
venv\Scripts\activate                        
pip install -r requirements.txt
```

Add inside `.env`:
```
GEMINI_API_KEY=your_api_key_here
```



##  Run the application

```bash
streamlit run app/main.py
```
Open → http://localhost:8501



##  Example Use

```
User: Who is the CEO of Google?
Bot: Sundar Pichai.

User: Where did he study?
Bot: Stanford University.

User: Tell me something positive.
Bot: (Search + reasoning response)
```


## Requirements

```
streamlit>=1.28.0
langchain>=0.1.0
google-generativeai>=0.4.0
ddgs>=1.1.5
python-dotenv>=1.0.1
requests>=2.32.0
pydantic>=1.10.14
```


