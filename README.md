# LangChain Document QA

This example provides an interface for asking questions to a PDF document. 

A ready to use 100% local setup 

## Setup

```shell
# pip install -r requirements.txt
# pipenv install -r requirements.txt
# Install from Pipfile
pipenv install
```

## Run

### Start Ollama

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



