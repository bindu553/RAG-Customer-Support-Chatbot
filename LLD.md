# Low-Level Design Document
## RAG-Based Customer Support Assistant

### 1. Module-Level Design

#### Module 1: Knowledge Base (SUPPORT_KNOWLEDGE)
```python
SUPPORT_KNOWLEDGE = {
    "returns_refunds": {
        "keywords": ["return", "refund", "money back"],
        "answer": "Full refund policy text...",
        "policy_details": "Additional details..."
    }
    # 7 more categories
]

```
Module 2: Intent Detection (detect_intent)
```
def detect_intent(question):
    # Input: String question
    # Output: (intent_name, confidence_score)
    # Process: Keyword matching with scoring
```
Module 3: RAG Retrieval (retrieve_answer)
```
def retrieve_answer(question, intent):
    # Input: User question, detected intent
    # Output: List of relevant answers
    # Process: Lookup intent in knowledge base
```
Module 4: Response Generation (generate_response)
```
def generate_response(question, intent, answers, confidence):
    # Input: All context data
    # Output: Formatted response string
    # Process: Template-based generation
```
Module 5: HITL Module (human_escalation)
```
def human_escalation(user_question, bot_response, reason):
    # Input: Question, bot response, escalation reason
    # Output: Human-provided response
    # Process: Console input simulation
```
2. Data Structures
```
# State Object
class SupportState:
    query: str                    # User's question
    intent: str                   # Detected intent
    confidence: float             # Confidence score (0-1)
    answers: List[str]           # Retrieved answers
    response: str                 # Generated response
    needs_human: bool             # Escalation flag

# Session Statistics
session_stats = {
    "total_queries": int,        # Total questions asked
    "human_escalations": int,    # Times escalated to human
    "intents_detected": dict     # Intent frequency count
}
```
3. Workflow Design (LangGraph Style)
┌─────────────────────────────────────────────────────────────┐
│                       WORKFLOW GRAPH                        │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   [START] → [INPUT NODE] → [INTENT NODE] → [ROUTER NODE]   │
│                                                   │         │
│                          ┌────────────────────────┼─────┐   │
│                          │                        │     │   │
│                          ▼                        ▼     │   │
│                   [RAG NODE]                 [HITL NODE] │   │
│                          │                        │     │   │
│                          └────────────┬───────────┘     │   │
│                                       ▼                 │   │
│                                [OUTPUT NODE]            │   │
│                                       │                 │   │
│                                       ▼                 │   │
│                                    [END]                │   │
└─────────────────────────────────────────────────────────────┘
4. Conditional Routing Logic
```
def route_decision(confidence, intent, answers):
    """
    Routing Rules:
    1. If confidence < 0.5 → ESCALATE TO HUMAN
    2. If answers empty → ESCALATE TO HUMAN
    3. If intent == "contact_support" → ESCALATE TO HUMAN
    4. If user_input == "human" → ESCALATE TO HUMAN
    5. Otherwise → USE RAG AUTO-RESPONSE
    """
    if confidence < 0.5:
        return "HUMAN"
    elif len(answers) == 0:
        return "HUMAN"
    elif intent == "contact_support":
        return "HUMAN"
    else:
        return "RAG"
```
5. HITL Design

Escalation Triggers:
Trigger	Condition
Low Confidence	confidence < 0.5
No Results	answers list empty
Direct Request	"human" in query
Contact Intent	intent == "contact_support"

Escalation Flow:
1. Detect trigger condition
2. Print escalation banner
3. Show customer question and bot attempt
4. Wait for human input
5. Return human response as answer
6. Log escalation in session stats

6. Error Handling
```
# Empty question
if not user_input:
    continue  # Ask again

# No intent matched
if intent == "general" and confidence < 0.3:
    escalate_to_human()

# Retrieval failure
if len(answers) == 0:
    use_fallback_response()
```
7. Interface Design

Input Format:

    Type: Plain text string

    Length: Any

    Commands: 'status', 'human', 'exit'
