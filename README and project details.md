# 🤖 RAG-Based Customer Support Assistant

## Project Overview
A complete RAG (Retrieval-Augmented Generation) customer support chatbot with Intent Detection, Human-in-the-Loop (HITL) Escalation, and Real-time Response Generation.

## 📸 Output Screenshots

### 1. Returns & Refunds Query

<img width="940" height="332" alt="image" src="https://github.com/user-attachments/assets/0920deb4-7aca-4df5-a07b-4b013361ae47" />

### 2. Shipping & Tracking Query
<img width="940" height="343" alt="image" src="https://github.com/user-attachments/assets/b27eed6c-afd3-4905-a2a8-aa920116eeb0" />


### 3. System Status

<img width="940" height="343" alt="image" src="https://github.com/user-attachments/assets/1a9e8f1c-dc0c-425f-9e58-e7f8cfc2b22f" />

### 4. Human-in-the-Loop (HITL) Escalation

<img width="940" height="345" alt="image" src="https://github.com/user-attachments/assets/08bc9429-8d2e-4207-8b9f-cba205a2a3bf" />

### 5. Session Summary on Exit
<img width="940" height="161" alt="image" src="https://github.com/user-attachments/assets/9f27e452-ac51-4886-868c-be6695fdf1db" />


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


