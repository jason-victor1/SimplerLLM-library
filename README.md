# Simplify AI Agent Building Using SimplerLLM

## Introduction to SimplerLLM
**SimplerLLM** is a lightweight Python library designed to simplify interaction with language models like OpenAI's GPT-4 or Anthropic's Claude.  
It eliminates the need for complex setups or multiple dependencies, offering a streamlined interface for building AI-powered applications.

---

## Installation
Ensure you are in a **virtual environment**, then install the library with the following command:
```bash
pip install simplerllm
```

---

## Setting Up the Instance
Import the library and create an instance of the language model:
```python
from simplerllm import Language

# Initialize the SimplerLLM instance
llm = Language(provider="openai", model_name="gpt-4")
```

### Key Advantage:
Changing the provider or model is as simple as updating the `provider` or `model_name` parameter:
```python
llm = Language(provider="anthropic", model_name="claude-v2")
```
This flexibility allows you to adapt your application without rewriting code.

---

## Generating Responses
Generate text or interact with the AI using a single function:
```python
messages = [{"role": "user", "content": "Tell me a joke!"}]
response = llm.generate_response(messages=messages)
print(response)
```

### Simplified Approach:
You don’t need to define the model repeatedly since it’s already set in the instance.

---

## Built-In Tools
**SimplerLLM** includes pre-built tools to replace common utilities like JSON helpers or text extraction functions:
```python
from simplerllm.tools import extract_data

# Example: Extract structured data from text
text = "The price of Bitcoin is $35,000."
structured_data = extract_data(text)
print(structured_data)
```
These tools reduce the need for external libraries or custom scripts.

---

## Code Simplification
By using **SimplerLLM**, you can eliminate:
- The need for managing separate helper functions like JSON parsers.
- Overhead of setting up providers or models for each interaction.

### Example of a Simplified Script:
```python
from simplerllm import Language

# Initialize the library
llm = Language(provider="openai", model_name="gpt-4")

# Generate a response
messages = [{"role": "user", "content": "What's the weather like in Boston?"}]
response = llm.generate_response(messages=messages)

print(response)
```

---

## Current Issue with SimplerLLM

### Dependency Conflict
There is a known issue with **SimplerLLM** version `0.3.1.1` due to a dependency conflict with the `openai` library:
- **Pinned Requirement:** `SimplerLLM 0.3.1.1` requires `openai==1.25.0`.
- **Conflict:** Installing or upgrading to `openai==1.59.3` results in the following error:
  ```text
  ERROR: pip's dependency resolver does not currently take into account all the packages ...
  simplerllm 0.3.1.1 requires openai==1.25.0, but you have openai 1.59.3 which is incompatible.
  ```

### Additional Issue:
- Using `openai==1.25.0` may result in a `TypeError` related to “proxies” in OpenAI’s client initialization.

---

### Developer Communication
The issue has been reported to the library creator, and the following response was provided:
> “Thanks for reporting this. Yeah, we noticed the same, and we will update it soon.”

### Questions Raised:
1. **Updating Dependencies:**  
   Is there a plan to update SimplerLLM’s OpenAI version pin to support newer releases (≥1.59.x)?
2. **Proxies in Client Initialization:**  
   Does SimplerLLM still rely on passing proxies to OpenAI’s client initialization, and could removing this parameter resolve the `TypeError`?

### Current Workaround:
- Use `openai==1.25.0` (but note the potential for `TypeError` issues).
- Avoid upgrading to `openai==1.59.3` until the library updates its dependency requirements.

If you experience similar issues or have additional insights, feel free to reach out to the library maintainer.

---

## Advantages for Scaling
- **Reusable and Scalable**: Ideal for projects involving multiple AI agents or tools.
- **Reduced Development Time**: Focus on core functionality rather than boilerplate setup.
- **Future-Proof**: Easily switch providers or models as new options emerge (pending resolution of the current dependency issue).

---

## Real-World Impact
**SimplerLLM** changes the way you build and manage AI applications. It’s particularly useful for building large-scale AI products and tools where simplicity, flexibility, and maintainability are crucial.

---

## Conclusion
By consolidating model interaction, tool integration, and dependency management, **SimplerLLM** serves as a game-changer for building AI agents efficiently.  
Start building your AI-powered applications today with **SimplerLLM** while staying updated on fixes for the current dependency issue.
