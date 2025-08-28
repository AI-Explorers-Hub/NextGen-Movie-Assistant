# ReAct Agents with Next Gen UI

A sophisticated AI agent system that combines movie search capabilities with dynamic UI generation using LangGraph and OpenAI's language models.

## Overview

This project demonstrates a multi-agent architecture where:
- **Movies Agent**: Searches for movie information and provides detailed responses
- **Next Gen UI Agent**: Transforms text responses into interactive UI components

The system showcases the ReAct (Reasoning + Acting) pattern, where agents can reason about problems and take actions to solve them.

## Features

- 🎬 **Movie Search**: Query movie information including plot, ratings, cast, and more
- 🎨 **Dynamic UI Generation**: Automatically generate UI components from text responses
- 🔧 **Multiple Component Systems**: Support for JSON and RHDS component rendering
- ⚡ **Async Processing**: Efficient async/await patterns for agent interactions
- 🤖 **ReAct Pattern**: Intelligent reasoning and action-taking capabilities

## Prerequisites

- Python 3.8+
- OpenAI API key
- Required Python packages (see Installation)

## Installation

1. Clone the repository:
```bash
git clone https://github.com/AI-Explorers-Hub/NextGen-Movie-Assistant.git
cd NextGen-Movie-Assistant
```

2. Install required dependencies:
```bash
pip install langchain-openai langgraph next-gen-ui-langgraph
```

3. (Optional) For RHDS component system:
```bash
pip install next-gen-ui-rhds-renderer
```

4. Set up your OpenAI API key:
```bash
export OPENAI_API_KEY="your-api-key-here"
```

## Usage

### Basic Usage

Run the demo script:
```bash
python next_gen.py
```

### Customizing Prompts

Edit the `prompt` variable in the `run()` function to try different queries:

```python
# Example prompts you can try:
prompt = "Play Toy Story movie trailer"
prompt = "Show me the poster of Toy Story"
prompt = "Tell me details about Toy Story, including poster"
```

### Component Systems

The system supports two component rendering modes:

- **JSON**: Basic JSON component structure
- **RHDS**: Red Hat Design System components (requires additional package)

Switch between them by modifying the `component_system` variable:

```python
component_system = "json"  # or "rhds"
```

## Architecture

### Movies Agent
- Uses LangGraph's `create_react_agent` with custom movie search tools
- Searches a predefined movie database (currently includes Toy Story)
- Returns structured movie information including ratings, cast, plot, etc.

### Next Gen UI Agent
- Transforms text responses into UI components
- Supports multiple rendering systems
- Generates interactive elements like trailers, posters, and movie details

## Example Output

The system produces two types of output:

1. **Text Response**: Natural language answer about the movie
2. **UI Component**: Structured component definition for rendering

```
===Movies Text Answer===
Based on the movie information for Toy Story, I can help you access the trailer...

===Next Gen UI rhds Rendition===
{
  "component": "video-player",
  "props": {
    "src": "https://www.youtube.com/watch?v=v-PjgYDrg70",
    "title": "Toy Story Trailer"
  }
}
```

## Configuration

### Environment Variables
- `OPENAI_API_KEY`: Your OpenAI API key (defaults to "ollama" if not set)

### Model Settings
- **Model**: `gpt-4o-mini` (configurable)
- **Temperature**: `0` for consistent responses

## Extending the System

### Adding New Movies
Extend the `movie_toy_story` list with additional movie data:

```python
movie_database = [
    # Add your movie objects here
    {
        "movie": {
            "title": "Your Movie",
            "year": 2023,
            # ... other properties
        }
    }
]
```

### Creating Custom Tools
Add new tools to the movies agent:

```python
def custom_tool(parameter: str):
    """Your custom tool description."""
    # Implementation here
    return result

movies_agent = create_react_agent(
    model=llm,
    tools=[search_movie, custom_tool],  # Add your tool
    prompt="Updated system prompt"
)
```

## Dependencies

- `langchain-openai`: OpenAI integration for LangChain
- `langgraph`: Graph-based agent framework
- `next-gen-ui-langgraph`: UI generation capabilities
- `asyncio`: Async processing support
- `json`: JSON handling
- `os`: Environment variable management

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## License

[Add your license information here]

## Support

For questions or issues, please open an issue on GitHub or contact the maintainers.

---

*This project demonstrates advanced AI agent patterns and serves as a foundation for building sophisticated multi-agent systems.*
