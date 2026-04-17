# Gemma4:e4b
To run the model on port 11434
```bash
docker run -p11434:11434 docker.io/frenoid/qwen3-embedding-0.6b:ollama-0.20.7
```
To create some beddings
```bash
curl http://localhost:11434/v1/embeddings \
  -H "Content-Type: application/json" \
  -d '{ "model": "qwen3-embedding:0.6b", "input": "Financial risk assessment for Q3 2026" }'
```
