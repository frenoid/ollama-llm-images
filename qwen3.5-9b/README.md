# Qwen3.5:9b
To run the model on port 11434
```bash
docker run -p11434:11434 docker.io/frenoid/qwen3.5-9b:ollama-0.21.0-amd64-nonroot
```
To send in a prompt
```bash
curl http://localhost:11434/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{ "model": "qwen3.5-9b", "messages": [{"role": "user", "content": "how many instance of the letter r are there in the word strawberry"}] }'
```
