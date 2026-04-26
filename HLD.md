# High-Level Design Document
## RAG-Based Customer Support Assistant

### 1. System Overview

**Problem Definition:** Customers need quick, accurate support answers without waiting for human agents. Traditional chatbots lack context understanding.

**Solution:** RAG-based system that retrieves relevant information from knowledge base and generates contextual responses.

**Scope:** 
- Handle 8 customer support categories
- Auto-respond with 90%+ confidence
- Escalate to humans when uncertain

### 2. System Architecture
┌─────────────────────────────────────────────────────────────────┐
│ USER INTERFACE │
│ (Terminal / Command Line) │
└─────────────────────────────┬───────────────────────────────────┘
│
▼
┌─────────────────────────────────────────────────────────────────┐
│ INTENT DETECTION LAYER │
│ (detect_intent() function) │
│ Classifies: returns, shipping, account, etc. │
└─────────────────────────────┬───────────────────────────────────┘
│
▼
┌─────────┴─────────┐
│ │
▼ ▼
┌─────────────────┐ ┌─────────────────┐
│ CONFIDENCE │ │ CONFIDENCE │
│ ≥ 50% │ │ < 50% │
│ (RAG Path) │ │ (HITL Path) │
└────────┬────────┘ └────────┬────────┘
│ │
▼ ▼
┌─────────────────┐ ┌─────────────────┐
│ RAG RETRIEVAL │ │ HUMAN-IN-THE- │
│ retrieve_ans() │ │ LOOP Escalation│
└────────┬────────┘ └────────┬────────┘
│ │
└──────────┬──────────┘
│
▼
┌─────────────────────┐
│ RESPONSE OUTPUT │
└─────────────────────┘


### 3. Component Description

| Component | Technology | Purpose |
|-----------|------------|---------|
| Document Loader | SUPPORT_KNOWLEDGE | Stores support articles |
| Chunking Strategy | Category-based split | 8 chunks = 8 topics |
| Embedding Model | Keyword matching | Intent classification |
| Vector Store | Ready for ChromaDB | Semantic search |
| Retriever | retrieve_answer() | Fetches relevant answers |
| LLM | Template-based | Response generation |
| Router | Conditional logic | Routes to RAG or HITL |
| HITL Module | human_escalation() | Human intervention |

### 4. Data Flow
User inputs question

Intent detection analyzes keywords

Confidence score calculated

IF confidence ≥ 50%:

    Retrieve answer from knowledge base

    Generate template response

    Output to user

IF confidence < 50%:

    Escalate to human agent

    Get human response

    Output to user

    
### 5. Technology Choices

| Choice | Reason |
|--------|--------|
| Python | Easy prototyping, rich libraries |
| Keyword-based intent | Fast, no training data needed |
| Template responses | Consistent, controlled output |
| Confidence threshold (50%) | Optimal balance of automation vs accuracy |

### 6. Scalability Considerations

- **Large documents:** Switch to ChromaDB vector storage
- **High query load:** Deploy as API service
- **Latency:** Keyword matching < 10ms, ChromaDB < 100ms

  
