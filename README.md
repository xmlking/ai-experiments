# LangChain Document QA

This example provides an interface for asking questions to a PDF document. 

A ready to use 100% local setup 

## Prerequisites 

1. [ollama](https://ollama.ai/) for mac installed.
2. Docker Desktop with 12GB RAM allocated

## Setup

```shell
# pip install -r requirements.txt
# pipenv install -r requirements.txt
# pipenv requirements > requirements.txt
# setup virtualenv
pipenv shell
# Install from Pipfile
pipenv install
```

### Pull some models
```shell
ollama pull mistral
ollama pull llama2
# verify
ollama list
```

### Run a model
```shell
ollama run mistral
```

### Call REST API

```shell
# Generate a response
curl http://localhost:11434/api/generate -d '{
  "model": "llama2",
  "prompt":"Why is the sky blue?"
}'

curl -X POST http://localhost:11434/api/generate -d '{
  "model": "mistral",
  "prompt": "Why is the sky blue?",
  "stream": false
}'

# (OR) Chat with a model
curl http://localhost:11434/api/chat -d '{
  "model": "mistral",
  "messages": [
    { "role": "user", "content": "why is the sky blue?" }
  ]
}'
```

## Run

### Start Ollama 

Start via **ollama** via docker, if you are not running it via CLI
```shell
docker compose up
open http://localhost:11434/
```

### Run a model

Now you can run a model like mistral inside the container.
```shell
docker exec -it ollama ollama run mistral
```

### Verify

Test if base model respond
```shell
curl -X POST http://localhost:11434/api/generate -d '{
  "model": "mistral",
  "prompt": "Why is the sky blue?",
  "stream": false
}'
```

### Start RAG
```shell
pipenv run python main.py
# (Or) You can activate the virtual environment then run the file
pipenv shell
python main.py
```

A prompt will appear, where questions may be asked:

```
Query: How many locations does WeWork have?
```



