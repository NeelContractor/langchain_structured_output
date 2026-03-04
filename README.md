# Structured Output in Langchain

This repository documents my learning and experiments with Structured Output in LangChain.

The goal of this project is to understand how to make Large Language Models (LLMs) return data in a well-defined format (like JSON) instead of free-form text.

## Why Structured Output?

By default, LLMs return plain text.
Plain text is hard to:

- Parse reliably
- Store in databases
- Validate
- Use in APIs or automation systems

Structured output solves this by enforcing formats such as:
- JSON
- Python dictionaries
- Pydantic models
- TypedDict schemas

## What I Learned
## 1. TypedDict

Used to define the expected structure of a dictionary.

from typing import TypedDict
```
class User(TypedDict):
    name: str
    age: int
```
- Lightweight
- Good for type hints
- No runtime validation

Best for small experiments and simple structure definitions.

## 2. Pydantic

Used for strong runtime validation and schema enforcement.

from pydantic import BaseModel
```
class User(BaseModel):
    name: str
    age: int
```
- Runtime validation
- Type conversion
- Production-ready
- Automatically converts to JSON Schema

Best for real-world applications and AI systems.

## 3. JSON Schema

Formal schema definition format.

Example:
```
{
  "type": "object",
  "properties": {
    "name": { "type": "string" },
    "age": { "type": "integer" }
  },
  "required": ["name", "age"]
}
```
- Standardized
- Used in tool/function calling
- Works across systems

Best for API-level schema definitions.