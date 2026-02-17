# Compliance Flow

An AI-powered blog generation system built with LangGraph and FastAPI that creates SEO-friendly blog content with multi-language translation support.

## Features

- **Automated Blog Generation**: Generate blog titles and content based on topics using AI
- **Multi-Language Support**: Translate blog content to Hindi and French
- **LangGraph Workflow**: Structured state management and conditional routing
- **FastAPI Backend**: RESTful API for blog generation
- **LangSmith Integration**: Monitor and debug your LangGraph workflows

## Architecture

The project uses LangGraph to orchestrate a multi-step blog generation workflow:

1. **Title Creation**: Generates SEO-friendly blog titles
2. **Content Generation**: Creates detailed blog content with markdown formatting
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

#### Generate Blog (Topic Only)

```bash
POST /blogs
Content-Type: application/json

{
  "topic": "Artificial Intelligence in Healthcare"
}
```

#### Generate Blog with Translation

```bash
POST /blogs
Content-Type: application/json

{
  "topic": "Artificial Intelligence in Healthcare",
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
│   │   └── blog_node.py        # Blog generation nodes
│   └── states/
│       └── blogstate.py        # State definitions
├── app.py                       # FastAPI application
├── main.py                      # Entry point
├── langgraph.json              # LangGraph configuration
├── requirements.txt            # Python dependencies
└── pyproject.toml              # Project metadata
```

## How It Works

1. **Topic-Based Generation**: Provide a topic, and the system generates a complete blog post
2. **Language Translation**: Optionally specify a language for automatic translation
3. **Conditional Routing**: LangGraph routes to the appropriate translation node based on language
4. **Structured Output**: Returns blog with title and content in markdown format

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
