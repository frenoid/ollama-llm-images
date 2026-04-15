# Gemma4:e2b
To run the model on port 11434
```bash
docker run -p11434:11434 docker.io/frenoid/gemma4-e2b:ollama-0.20.7
```
To send in a prompt
```bash
curl http://localhost:11434/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{ "model": "gemma4:e2b", "messages": [{"role": "user", "content": "how many instance of the letter r are there in the word strawberry"}] }'
```
