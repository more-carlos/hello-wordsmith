# Hello Wordsmith (Ollama Version)

This is a modified **Hello Wordsmith** package using a local model instead of OpenAI. Since I don't have an OpenAI subscription, this fork will allow to execute the Hello Wordsmith project using a model installed locally through Ollama.

This is a simple wrapper around the `llama-index CLI` project with some opinionated defaults. We aim to provide a "Hello World" experience using Retrieval-Augmented Generation (RAG). For more context on what RAG is, tradeoffs and, and a detailed walthrough of this project, see [this The Pragmatic Engineer article](https://newsletter.pragmaticengineer.com/p/rag). 

For detailed information about the `llamaindex-rag` project, visit the [official documentation](https://docs.llamaindex.ai/en/stable/getting_started/starter_tools/rag_cli/).

## Pre-requisites for usage

- [Ollama](https://ollama.com) running a model locally in your machine. In the [Ollama Github repo](https://github.com/ollama/ollama) you can find all the information you need to run a model in your local machine.
- For better performance, `llama3.2` is recommended over `llama2` (which can be quite slow).
- Python 3.9 installed (e.g., `brew install python@3.9` on macOS)
- Hardware requirements:
  - Minimum: 8GB RAM, modern CPU
  - Recommended: 16GB+ RAM, recent CPU or GPU for faster inference. It worked fine on a MacBook Pro 16 M3 Pro with 36GB

## Installation

Follow these steps to install and set up your environment:

### Basic Installation
1. `pip install git+https://github.com/more-carlos/hello-wordsmith -q`

Note: It's best practice to work in a virtual Python environment, as opposed to your system's default Python installation. Popular solutions include `venv`, `conda`, and `pipenv`. If you *do* use your system Python, make sure the bin dir is on your PATH, e.g. `export PATH="/Library/Frameworks/Python.framework/Versions/3.x/bin:${PATH}"`

### Using Poetry
If you prefer using Poetry for environment management:
1. `poetry env use $(which python3.9)` to create an environment
2. `poetry env activate` to activate the environment
3. `poetry install` to install dependencies

## Usage

1. `hello-wordsmith` // Launch an interactive chat.
2. `hello-wordsmith -q 'What is article III about?'` // Single question and answer
3. `hello-wordsmith -f "./my_directory/*" --chunk-size 256 --chunk-overlap 128` // Ingest and index your own data to query with custom document chunk sizes and overlaps
4. `hello-wordsmith --clear` // Clear stored data

## Example installation and usage via venv

<img width="509" alt="example" src="https://github.com/wordsmith-ai/hello-wordsmith/assets/1094502/beb3df38-734f-49b0-9d46-5d6386779e71">

## Troubleshooting

- **Checking if Ollama is running**: Before using hello-wordsmith, verify that Ollama is running with: `curl http://localhost:11434/api/tags`
- **Timeout errors**: If you encounter timeout errors, try using a smaller model like `llama3.2` instead of larger models
- **OpenAI errors**: If you see errors related to OpenAI API, ensure environment variables are correctly set (this should be handled automatically by this fork)
- **Dependency issues**: If you encounter dependency conflicts, try recreating your environment or using the exact versions specified in the pyproject.toml file

## Explore

As you can see, this repo is an extremely simplistic first step towards building a RAG system on your data. You can open up these files and explore how changing parameters like chunk size, or the embedding model that we use, can influence the performance of the system.

## Development Tools

As I am a little bit rusty with Python, I used this project to test [Cursor](https://cursor.sh/), an AI-powered code editor. Cursor significantly improved the development process by providing intelligent code suggestions, helping with debugging and fixing issues. It was a little messy with some dependencies issues, but in general the experience was quite positive
