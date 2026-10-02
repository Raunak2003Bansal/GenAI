# Zero-One-Few Shot Prompting

This project demonstrates how to use zero-shot, one-shot, and few-shot prompting patterns with a simple AI-powered complaint routing example.

## File

- `Zero_One_Few_Shot_Prompting.ipynb`

## What this notebook does

The notebook builds a prompt that instructs a model to act as a banking customer service router. It classifies customer complaints into categories such as:

- Cards
- Loans
- NetBanking
- Accounts
- Fraud
- KYC

For each complaint, the model returns a JSON object containing:

- `department`
- `priority`
- `suggested_action`

The example includes:

- a system instruction defining the routing behavior
- multiple few-shot examples
- a real customer complaint to classify
- output printing for the final result

## Example workflow

The notebook defines a message list like this:

```python
complaint_messages = [
    {
        "role": "system",
        "content": (
            "You are a banking customer service router. "
            "Classify each complaint and return JSON with: "
            "department (Cards / Loans / NetBanking / Accounts / Fraud / KYC), "
            "priority (High / Medium / Low), and a one-line suggested_action."
        )
    },
    {"role": "user", "content": "My credit card was charged twice for the same order at Zomato yesterday."},
    {"role": "assistant", "content": '{"department": "Cards", "priority": "High", "suggested_action": "Initiate chargeback process and credit provisional refund within 24 hours."}'},
    # ... more examples ...
    {"role": "user", "content": "My home loan EMI was deducted twice this month and my account balance is now negative."}
]
```

Then it calls:

```python
result = chat_with_model(complaint_messages)
print(result)
```

## Sample output

```json
{"department": "Loans", "priority": "High", "suggested_action": "Reverse the duplicate EMI deductions and credit the account within 24 hours to prevent further financial impact."}
```

## Why this matters

This notebook is a practical example of few-shot prompting, where the model is guided by a few labeled examples before being asked to solve a new task. This is useful for:

- intent classification
- customer support routing
- document triage
- structured JSON extraction
- rule-based assistance with LLMs

## Notes

This notebook assumes a helper function such as:

```python
def chat_with_model(messages: list[dict], model: str = "qwen3:4b") -> str:
    response = chat(model=model, messages=messages)
    return response
```

Make sure the model provider or chat function is available in your environment before running the notebook.
