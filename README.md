# Agentic College Assistant

An intelligent AI-powered college assistant built using LangGraph, Retrieval-Augmented Generation (RAG), FAISS, and Streamlit.

The system automatically classifies student queries and conditionally routes them to the appropriate knowledge source for accurate and context-aware responses.

## Overview

College students frequently need information related to academic policies, attendance requirements, examinations, fee structures, scholarships, and general campus queries.

Traditional chatbots often rely on a single knowledge source or generate responses without verifying institutional information.

The Agentic College Assistant solves this problem using a conditional RAG architecture powered by LangGraph.

The application first analyzes the user's query and classifies it into one of three categories:

- Academic
- Fee
- General

Based on the detected query type, LangGraph dynamically routes the query to the appropriate processing path.

# Features
- Intelligent query classification
- Conditional routing using LangGraph
- Retrieval-Augmented Generation (RAG)
- Separate academic and fee knowledge bases
- FAISS-based semantic vector search
- Hugging Face sentence embeddings
- Groq-powered LLM responses
- Programme-aware personalized answers
- Conversational chat interface
- Persistent chat history using Streamlit session state
- Query classification badges
- Cached vector stores and graph resources

##  System Architecture

The application follows a conditional agentic workflow:

```text
                         ┌─────────────────┐
                         │   User Query    │
                         └────────┬────────┘
                                  │
                                  ▼
                         ┌─────────────────┐
                         │ Classifier Node │
                         └────────┬────────┘
                                  │
               ┌──────────────────┼──────────────────┐
               │                  │                  │
               ▼                  ▼                  ▼
      ┌────────────────┐ ┌────────────────┐ ┌────────────────┐
      │  Academic RAG  │ │    Fee RAG     │ │  General Node  │
      └────────┬───────┘ └────────┬───────┘ └────────┬───────┘
               │                  │                  │
               └──────────────────┼──────────────────┘
                                  │
                                  ▼
                         ┌─────────────────┐
                         │  Response Node  │
                         └────────┬────────┘
                                  │
                                  ▼
                         ┌─────────────────┐
                         │  Final Answer   │
                         └─────────────────┘
```

##  LangGraph Workflow

The workflow is implemented as a state graph.

1. Classifier Node

The classifier analyzes the latest user query and categorizes it as:

- academic
- fee
- general

2. Conditional Router

The router dynamically selects the next node based on the query category.

3. Academic RAG Node

Retrieves relevant information from the academic handbook using FAISS semantic search.

4. Fee RAG Node

Retrieves relevant information from the fee structure document.

5. General Node

Handles greetings, casual conversation, and general queries without document retrieval.

6. Response Node

Generates the final answer using the Groq-hosted LLM and the retrieved context.

##  Tech Stack

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| LangGraph | Agent workflow and conditional routing |
| LangChain | RAG components and document processing |
| Groq | LLM inference |
| Llama 3.3 70B | Response generation and query classification |
| FAISS | Vector similarity search |
| Hugging Face | Sentence embeddings |
| MiniLM | Text embedding model |
| Streamlit | Interactive web interface |
| PyPDF | PDF document loading |

##  Project Structure

```text
agentic_ai/
│
├── app.py
├── conditional_rag.py
├── academics_handbook.pdf
├── fee_structure.pdf
├── requirements.txt
├── .env.example
├── .gitignore
└── README.md
```
## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/meharr22/smart_college_chatbot.git
```

### 2. Create a Virtual Environment

```bash
python -m venv venv
```

### 3. Activate the Virtual Environment

For Windows:

```bash
venv\Scripts\activate
```

For macOS/Linux:

```bash
source venv/bin/activate
```

### 4. Install Dependencies

```bash
pip install -r requirements.txt
```

### 5. Configure Environment Variables

Create a `.env` file in the root directory of the project.

```env
GROQ_API_KEY=your_groq_api_key_here
```

### 6. Run the Application

```bash
python -m streamlit run app.py
```

The College Assistant will launch in your browser.

---

## Use Cases

The Agentic College Assistant can help students quickly access information from institutional documents without manually searching through lengthy PDFs.

### Academic Policy Assistance

### Fee and Financial Information

### Programme-Specific Assistance

### General Student Assistance

### Potential Institutional Use

## Author

### Mehar Arora
