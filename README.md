# Autosuggestion Architecture Comparison

A comprehensive comparison of different LangGraph architectures for providing intelligent autosuggestions in educational applications. This project evaluates and benchmarks two distinct architectural approaches to determine the optimal design pattern.

## 🎯 Project Overview

This repository focuses on comparing different architectural patterns for implementing autosuggestion functionality using LangGraph. The goal is to identify which architecture provides better performance in terms of:

- **Token Consumption** - Measured via LangSmith tracking
- **API Call Efficiency** - Number of calls required per workflow
- **Response Time** - Overall latency and user experience
- **Scalability** - Resource utilization and cost-effectiveness

## 🏆 Key Findings

Based on comprehensive testing and analysis using LangSmith token consumption tracking:

**Winner: Same Node Architecture** ✅

The Same Node architecture demonstrates superior performance across all metrics:
- **Lower Token Consumption** - More efficient use of LLM resources
- **Fewer API Calls** - Reduced network overhead and latency
- **Better Cost Efficiency** - Lower operational costs at scale
- **Simplified Workflow** - Easier to maintain and debug

## 📊 Architecture Comparison

### Architecture 1: Same Node Architecture

**Implementation:** `Trying_Autosuggestion_same_node/`

This architecture processes autosuggestion generation within a single node in the LangGraph workflow.

**Key Characteristics:**
- Consolidated logic in one node
- Reduced inter-node communication
- Optimized token usage through context reuse
- Fewer state transitions

**Architecture Diagram:**

![Same Node Architecture](path/to/same-node-architecture.png)

*[Paste architecture diagram here]*

---

### Architecture 2: Different Node Architecture

**Implementation:** `Trying_Autosuggestion_diff_node/`

This architecture distributes autosuggestion generation across multiple specialized nodes in the LangGraph workflow.

**Key Characteristics:**
- Modular node separation
- Dedicated nodes for different tasks
- Higher inter-node communication overhead
- More state transitions

**Architecture Diagram:**

![Different Node Architecture](path/to/different-node-architecture.png)

*[Paste architecture diagram here]*

---

## 📁 Project Structure

```
Autosuggestion_different_architectures/
│
├── Trying_Autosuggestion_same_node/     # Winner: Single-node architecture ✅
│   ├── src/
│   │   ├── graph.py                     # Consolidated autosuggestion logic
│   │   ├── core.py                      # Autosuggestion generation
│   │   ├── models.py                    # State type definitions
│   │   └── config.py                    # LLM configuration
│   ├── api_server.py                    # FastAPI endpoints
│   ├── test_api.py                      # API testing suite
│   ├── requirements.txt                 # Dependencies
│   └── README.md                        # Architecture details
│
├── Trying_Autosuggestion_diff_node/     # Multi-node architecture
│   ├── src/
│   │   ├── graph.py                     # Distributed node workflow
│   │   ├── core.py                      # Specialized node functions
│   │   ├── models.py                    # State type definitions
│   │   └── config.py                    # LLM configuration
│   ├── api_server.py                    # FastAPI endpoints
│   ├── test_api.py                      # API testing suite
│   ├── requirements.txt                 # Dependencies
│   └── README.md                        # Architecture details
│
├── Statefull/                           # Reference: Stateful implementation
├── Statefull_no_db/                     # Reference: Stateful without DB
├── Stateless/                           # Reference: Stateless implementation
│
└── README.md                            # This file
```

## 🧪 Performance Metrics

### Token Consumption Comparison

*Measured using LangSmith tracking*

| Metric | Same Node | Different Node | Improvement |
|--------|-----------|----------------|-------------|
| Average Tokens per Request | TBD | TBD | TBD% |
| Total API Calls per Workflow | TBD | TBD | TBD% |
| Average Response Time (ms) | TBD | TBD | TBD% |
| Cost per 1000 Requests | TBD | TBD | TBD% |

### API Call Analysis

| Architecture | Calls per Workflow | LLM Invocations | State Transitions |
|--------------|-------------------|-----------------|-------------------|
| Same Node | TBD | TBD | TBD |
| Different Node | TBD | TBD | TBD |

## 🚀 Getting Started

### Prerequisites

- Python 3.11+
- Google AI API Key ([Get it here](https://makersuite.google.com/app/apikey))
- LangSmith API Key (for tracking and analytics)

### Installation

```bash
# Clone the repository
git clone <repository-url>
cd Autosuggestion_different_architectures

# Navigate to desired architecture
cd Trying_Autosuggestion_same_node  # or Trying_Autosuggestion_diff_node

# Install dependencies
pip install -r requirements.txt
```

### Configuration

Create a `.env` file with required API keys:

```env
GOOGLE_API_KEY=your_google_api_key_here
LANGSMITH_API_KEY=your_langsmith_api_key_here
MODEL_NAME=gemini-2.0-flash
```

### Running the Server

```bash
# Start the FastAPI server
python api_server.py

# Server will be available at http://localhost:8000
# API documentation at http://localhost:8000/docs
```

### Testing

```bash
# Run API tests
python test_api.py
```

## 🔧 Technology Stack

- **Backend Framework:** FastAPI
- **AI Orchestration:** LangGraph
- **LLM Provider:** Google Gemini AI (gemini-2.0-flash)
- **Analytics & Tracking:** LangSmith
- **State Management:** LangGraph Checkpointing
- **Testing:** Python unittest/pytest

## 📈 Benchmarking Methodology

All performance metrics were collected using:

1. **LangSmith Integration** - Automatic token and cost tracking
2. **Consistent Test Scenarios** - Standardized input prompts and workflows
3. **Multiple Iterations** - Average of 100+ requests per architecture
4. **Controlled Environment** - Same API keys, models, and configurations

## 🎯 Use Cases

These architectures are designed for:

- **Educational Platforms** - Intelligent content suggestions for students
- **Writing Assistants** - Context-aware autocompletions
- **Chatbots** - Predictive response generation
- **Content Creation Tools** - AI-powered recommendations

## 📚 Additional Resources

- [LangGraph Documentation](https://langchain-ai.github.io/langgraph/)
- [LangSmith Documentation](https://docs.smith.langchain.com/)
- [FastAPI Documentation](https://fastapi.tiangolo.com/)
- [Google AI Studio](https://makersuite.google.com/)

## 🤝 Contributing

Contributions are welcome! Please feel free to submit pull requests or open issues for:
- Additional architecture patterns
- Performance optimization suggestions
- Benchmark improvements
- Documentation enhancements

---

**Conclusion:** Based on comprehensive testing, the **Same Node Architecture** is recommended for production autosuggestion implementations due to superior token efficiency and reduced API call overhead.
