# AI Chatbot using LangGraph

An intelligent AI chatbot built using **LangGraph**, **LangChain**, **Hugging Face Llama 3.1**, and **Streamlit**. The chatbot follows an agent-based architecture capable of maintaining persistent conversations, managing multiple chat threads, streaming responses in real time, and intelligently invoking external tools whenever required.

The application demonstrates how LangGraph can be used to orchestrate LLM reasoning, tool execution, and conversational memory within a single workflow.

---

## Features

### Conversational AI
- Natural language interaction powered by **Meta Llama 3.1 8B Instruct**.
- Context-aware conversations using conversation history.
- Intelligent reasoning before generating responses.

### Agentic Workflow
- Built using **LangGraph's StateGraph**.
- Uses conditional routing to determine whether a user query requires tool execution.
- Automatically switches between the language model and external tools.

### Persistent Memory
- Conversation history is stored using **LangGraph Checkpointing**.
- SQLite is used as the persistent storage backend.
- Users can continue conversations without losing previous context.

### Multi-Threaded Conversations
- Supports multiple independent chat sessions.
- Each thread maintains its own conversation history.
- Previously created chat threads can be retrieved and resumed.

### Real-Time Response Streaming
- Responses are streamed token-by-token, providing a smoother conversational experience.
- Reduces perceived response latency.

### Tool Integration

The chatbot is equipped with three tools that the language model can invoke whenever required.

#### Online Search Tool
- Performs real-time web searches using **DuckDuckGo Search**.
- Useful for answering queries requiring recent or external information beyond the language model's knowledge.

#### Calculator Tool
- Performs arithmetic operations including:
  - Addition
  - Subtraction
  - Multiplication
  - Division
- Includes validation for invalid operations and division-by-zero errors.

#### Stock Price Tool
- Retrieves the latest stock market data for a given stock symbol.
- Uses the **Alpha Vantage API** to fetch real-time stock prices and market information.

---

## Technologies Used

| Technology | Purpose |
|------------|---------|
| Python | Programming Language |
| LangGraph | Agent workflow orchestration |
| LangChain | LLM framework and tool integration |
| Hugging Face Inference API | Accessing the Llama 3.1 language model |
| Meta Llama 3.1 8B Instruct | Large Language Model |
| Streamlit | Interactive web interface |
| DuckDuckGo Search | Web search functionality |
| Alpha Vantage API | Stock market data |
| SQLite | Persistent conversation storage |
| Requests | API communication |
| python-dotenv | Environment variable management |

---

## Project Structure

```
.
├── langgraph_tool_backend.py
└── streamlit_frontend_threading.py
```

---

## How It Works

1. The user submits a query through the Streamlit interface.
2. The query is passed to the LangGraph workflow.
3. The language model determines whether an external tool is required.
4. If necessary, the appropriate tool is executed.
5. The tool output is passed back to the language model.
6. The final response is streamed to the user.
7. The conversation is automatically saved in SQLite using LangGraph checkpointing.

---

## Example Queries

- What is the capital of Australia?
- Search for the latest AI news.
- Calculate 345 × 27.
- Divide 250 by 8.
- What is the current stock price of AAPL?
- Get the latest stock price of TSLA.
- Search for recent developments in LangGraph.

---

## Future Improvements

- Retrieval-Augmented Generation (RAG)
- PDF and document question answering
- Voice input and speech synthesis
- Authentication and multi-user support
- Additional external tools
- Chat export functionality
- Conversation summarization
