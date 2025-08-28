# HTML News Content Processor with Ollama

This project processes Facebook news HTML files to extract relevant content and uses Ollama for structured data extraction.

## Features

- **HTML Content Extraction**: Clean and extract text from Facebook news HTML files
- **Smart Filtering**: Only extracts content from `div` tags with `style` attributes containing substantial text (>20 characters)
- **Ollama Integration**: Uses local LLM models to extract structured data (post content, likes, comments)
- **Jupyter Notebook Interface**: Interactive development and testing environment

## Files

- `main.ipynb` - Main Jupyter notebook with extraction and processing logic
- `requirements.txt` - Python dependencies
- `Dockerfile` - Docker configuration for Jupyter + Ollama environment
- `.gitignore` - Git ignore rules for Python/Jupyter/Docker/Ollama
- `.dockerignore` - Docker ignore rules

## Setup

### Local Setup
```bash
# Install dependencies
pip install -r requirements.txt

# Make sure Ollama is running with your preferred model
ollama pull qwen2.5:7b
```

### Docker Setup
```bash
# Build and run the container
docker build -t html-processor .
docker run -p 8888:8888 html-processor
```

## Usage

1. Place your Facebook news HTML files in the `news/` directory
2. Run the Jupyter notebook cells to:
   - Extract cleaned content from HTML files
   - Process content with Ollama for structured extraction
   - Get JSON output with post content, likes, and comments

## HTML Processing Strategy

The extraction function:
1. Removes unwanted tags (`script`, `style`, `head`)
2. Removes all `class` attributes to reduce noise
3. Finds `div` tags with `style` attributes in the body
4. Filters content by minimum length (20+ characters)
5. Returns clean, focused text for LLM processing

## Ollama Integration

- Uses Qwen2.5 7B model (32K context window)
- Structured JSON output format
- Extracts: post content, likes count, comments count
- Handles missing information gracefully

## Requirements

- Python 3.8+
- BeautifulSoup4 for HTML parsing
- Ollama for LLM processing
- Jupyter for interactive development
