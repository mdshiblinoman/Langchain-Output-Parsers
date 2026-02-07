# LangChain Output Parsers

A collection of examples demonstrating different output parsers in LangChain for structuring LLM responses.

## Prerequisites

- Python 3.8+
- HuggingFace account (for API token)
- OpenAI account (optional, for OpenAI examples)

## Installation

### Step 1: Clone the Repository

```bash
git clone <repository-url>
cd LangChainOutputParsers
```

### Step 2: Create a Virtual Environment

```bash
python -m venv venv
source venv/bin/activate  # On Linux/Mac
# OR
venv\Scripts\activate  # On Windows
```

### Step 3: Install Dependencies

```bash
pip install langchain langchain-huggingface langchain-openai python-dotenv pydantic
```

### Step 4: Set Up Environment Variables

Create a `.env` file in the project root:

```env
HUGGINGFACEHUB_API_TOKEN=your_huggingface_api_token
OPENAI_API_KEY=your_openai_api_key  # Optional, only for stroutputparser1.py
```

## Output Parsers Overview

### 1. String Output Parser (Basic)

**File:** `stroutputparser.py`

Demonstrates basic LLM chaining without using the LCEL (LangChain Expression Language) pipe syntax.

```bash
python stroutputparser.py
```

**What it does:**
- Creates a detailed report on a topic
- Summarizes the report into 5 lines
- Uses HuggingFace's Gemma model

---

### 2. String Output Parser (with LCEL)

**File:** `stroutputparser1.py`

Shows how to use `StrOutputParser` with LCEL chain syntax for cleaner code.

```bash
python stroutputparser1.py
```

**What it does:**
- Chains multiple prompts using the `|` operator
- Converts LLM output to plain string format
- Uses OpenAI's ChatGPT model

---

### 3. JSON Output Parser

**File:** `jsonoutputparser.py`

Parses LLM output into JSON format automatically.

```bash
python jsonoutputparser.py
```

**What it does:**
- Requests facts about a topic
- Automatically formats output as JSON
- Returns a Python dictionary

---

### 4. Pydantic Output Parser

**File:** `pydanticoutputparser.py`

Validates and structures LLM output using Pydantic models.

```bash
python pydanticoutputparser.py
```

**What it does:**
- Defines a `Person` schema with validation rules
- Ensures output matches the expected structure
- Provides type safety with field validation (e.g., age > 18)

---

### 5. Structured Output Parser

**File:** `structuredoutputparser.py`

Creates structured output using predefined response schemas.

```bash
python structuredoutputparser.py
```

**What it does:**
- Defines multiple response fields using `ResponseSchema`
- Returns output as a structured dictionary
- Useful for extracting specific information

---

## Usage Examples

### Running a Script

```bash
# Activate virtual environment
source venv/bin/activate

# Run any example
python jsonoutputparser.py
```

### Modifying Topics

Each script accepts different input parameters. For example, in `jsonoutputparser.py`:

```python
result = chain.invoke({'topic': 'artificial intelligence'})
```

## Project Structure

```
LangChainOutputParsers/
├── stroutputparser.py      # Basic string output (no LCEL)
├── stroutputparser1.py     # String output with LCEL chains
├── jsonoutputparser.py     # JSON formatted output
├── pydanticoutputparser.py # Pydantic validated output
├── structuredoutputparser.py # Schema-based structured output
├── .env                    # Environment variables (create this)
└── README.md               # This file
```

## Troubleshooting

### Common Issues

1. **API Token Error**: Ensure your `.env` file contains valid API tokens
2. **Module Not Found**: Run `pip install <module-name>` for missing packages
3. **Rate Limiting**: HuggingFace free tier has rate limits; wait and retry

### Getting HuggingFace API Token

1. Go to [HuggingFace](https://huggingface.co/)
2. Create an account or sign in
3. Navigate to Settings → Access Tokens
4. Create a new token with read permissions

## License

MIT License
