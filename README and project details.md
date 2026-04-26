 🤖 RAG-Based Customer Support Assistant

## Project Overview
A complete RAG (Retrieval-Augmented Generation) customer support chatbot with:
- ✅ Intent Detection & Routing
- ✅ Human-in-the-Loop (HITL) Escalation  
- ✅ RAG Implementation
- ✅ Real-time Response Generation

Architecture
User Input → Intent Detection → RAG Retrieval → Response → HITL 

 Features
| Feature | Description |
|---------|-------------|
| RAG | Retrieves relevant answers from knowledge base |
| Intent Detection | Identifies customer intent (returns, shipping, account, etc.) |
| HITL | Escalates to human when confidence < 50% |
| Vector Search | Uses embeddings for semantic search |

Sample Conversation
👤 Customer: I want to return my product
🎯 Intent: returns_refunds | Confidence: 90%
🤖 Assistant: I understand you need help with a return or refund. You can return items within 30 days...

👤 Customer: Where is my order?
🎯 Intent: shipping_delivery | Confidence: 90%
🤖 Assistant: Let me help with shipping. Standard shipping takes 3-5 business days...

👤 Customer: human
🔄 Transferring to human support...
👨‍💼 Agent: How can I help you today?

 How to Run

### Google Colab (Recommended)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/)

Tech Stack
RAG Framework: Custom implementation

Intent Detection: Keyword-based classification

HITL: Confidence-based escalation

Language: Python 3.x

Author
[Bindu]
