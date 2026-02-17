# Compliance Flow

An AI-powered compliance document generation system built with LangGraph and FastAPI that creates comprehensive compliance documentation with multi-language translation support.

## Features

- **Automated Compliance Document Generation**: Generate compliance document titles and content based on topics using AI
- **Multi-Language Support**: Translate compliance documents to Hindi and French
- **LangGraph Workflow**: Structured state management and conditional routing
- **FastAPI Backend**: RESTful API for compliance document generation
- **LangSmith Integration**: Monitor and debug your LangGraph workflows

## Architecture

The project uses LangGraph to orchestrate a multi-step compliance document generation workflow:

1. **Title Creation**: Generates professional compliance document titles
2. **Content Generation**: Creates detailed compliance documentation with markdown formatting
3. **Translation** (optional): Translates content to specified language (Hindi/French)
4. **Routing**: Conditionally routes to appropriate translation node

## Tech Stack

- **LangChain & LangGraph**: Workflow orchestration and state management
- **Groq LLM**: Language model for content generation
- **FastAPI**: Web framework for API endpoints
- **Uvicorn**: ASGI server
- **Python 3.13+**: Core programming language

## Installation

1. Clone the repository:
```bash
git clone https://github.com/Kshitij-AI-Architect/Compliance-Flow.git
cd Compliance-Flow
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Set up environment variables:

Create a `.env` file in the root directory with:
```env
GROQ_API_KEY=your_groq_api_key
LANGCHAIN_API_KEY=your_langchain_api_key
```

## Usage

### Running the API Server

```bash
python app.py
```

The server will start at `http://0.0.0.0:8000`

### API Endpoints

#### Generate Compliance Document (Topic Only)

```bash
POST /blogs
Content-Type: application/json

{
  "topic": "GDPR Data Protection Compliance"
}
```

#### Generate Compliance Document with Translation

```bash
POST /blogs
Content-Type: application/json

{
  "topic": "GDPR Data Protection Compliance",
  "language": "hindi"
}
```

Supported languages: `hindi`, `french`

### Using LangGraph Studio

The project includes LangGraph configuration for visual workflow debugging:

```bash
langgraph dev
```

## Project Structure

```
Compliance-Flow/
├── src/
│   ├── graphs/
│   │   └── graph_builder.py    # LangGraph workflow definitions
│   ├── llms/
│   │   └── groqllm.py          # Groq LLM configuration
│   ├── nodes/
│   │   └── blog_node.py        # Compliance document generation nodes
│   └── states/
│       └── blogstate.py        # State definitions
├── app.py                       # FastAPI application
├── main.py                      # Entry point
├── langgraph.json              # LangGraph configuration
├── requirements.txt            # Python dependencies
└── pyproject.toml              # Project metadata
```

## How It Works

1. **Topic-Based Generation**: Provide a compliance topic, and the system generates a complete compliance document
2. **Language Translation**: Optionally specify a language for automatic translation
3. **Conditional Routing**: LangGraph routes to the appropriate translation node based on language
4. **Structured Output**: Returns compliance document with title and content in markdown format

## Development

The project uses:
- **State Management**: TypedDict-based state for type safety
- **Pydantic Models**: Structured output validation
- **Conditional Edges**: Dynamic routing based on language selection
- **Hot Reload**: Uvicorn auto-reload for development

## License

MIT License

## Author

Kshitij Saxena ([@Kshitij-AI-Architect](https://github.com/Kshitij-AI-Architect))
