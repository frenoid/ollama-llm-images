# Gemma4:26b
To run the model on port 11434
```bash
docker run -p11434:11434 docker.io/frenoid/gemma4-26b:ollama-0.21.0-amd64-nonroot
```
To send in a prompt
```bash
curl http://localhost:11434/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{ "model": "gemma4-26b", "messages": [{"role": "user", "content": "how many instance of the letter r are there in the word strawberry"}] }'
```
