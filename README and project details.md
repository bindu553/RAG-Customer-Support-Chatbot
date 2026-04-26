# 🤖 RAG-Based Customer Support Assistant

## Project Overview
A complete RAG (Retrieval-Augmented Generation) customer support chatbot with Intent Detection, Human-in-the-Loop (HITL) Escalation, and Real-time Response Generation.

## 📸 Output Screenshots

### 1. Returns & Refunds Query
![Returns Query](images/return-query.png)

### 2. Shipping & Tracking Query
![Shipping Query](images/shipping-query.png)

### 3. System Status
![System Status](images/status.png)

### 4. Human-in-the-Loop (HITL) Escalation
![HITL](images/hitl.png)

### 5. Session Summary on Exit
![Exit Summary](images/exit-summary.png)

## Sample Conversation
👤 Customer: I want to return my product
🎯 Intent: returns_refunds | Confidence: 90%
🤖 Assistant: You can return items within 30 days of purchase for a full refund...

👤 Customer: Where is my order?
🎯 Intent: shipping_delivery | Confidence: 90%
🤖 Assistant: Standard shipping takes 3-5 business days...

👤 Customer: status
📊 System Status: Queries processed: 2 | Human handoffs: 0

👤 Customer: human
🔄 Transferring to human support...
👨‍💼 Agent: How can I help you?

👤 Customer: exit
📊 Bot Resolution Rate: 100%

## Architecture
User Input → Intent Detection → RAG Retrieval → Response Generation → HITL 


## Features
| Feature | Description |
|---------|-------------|
| **RAG** | Retrieves relevant answers from knowledge base |
| **Intent Detection** | Identifies customer intent (returns, shipping, account, warranty, etc.) |
| **HITL** | Escalates to human when confidence < 50% |
| **Session Stats** | Tracks queries, escalations, and resolution rate |

## Support Categories
- 🔄 Returns & Refunds
- 📦 Shipping & Delivery
- 🔐 Account Management
- 📝 Order Management
- 🛡️ Warranty
- 💬 Contact Support
- 💳 Payment & Billing
- 📋 Product Information

## How to Run

### Google Colab (Recommended)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/)

1. Click the badge above
2. Run all cells
3. Start chatting!

### Local Python
```bash
python rag_chatbot.py
```
Tech Stack
Language: Python 3.x

RAG: Custom implementation with intent-based retrieval

HITL: Confidence-based human escalation

Storage: In-memory knowledge base (extendable to vector DB)

Author
[Bindu]


