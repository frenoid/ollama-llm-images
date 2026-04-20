# Gemma4:e4b
To run the model on port 11434
```bash
docker run -p11434:11434 -d frenoid/embeddinggemma-300m:ollama-0.20.7-amd64
```
To create some embeddings
```bash
curl http://localhost:11434/v1/embeddings \
  -H "Content-Type: application/json" \
  -d '{ "model": "embeddinggemma:300m", "input": "Financial risk assessment for Q3 2026" }'
```
