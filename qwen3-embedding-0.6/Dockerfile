# Stage 1: Model downloader
FROM ollama/ollama:0.20.7 AS downloader

# Prevent Ollama from trying to use a GPU during build
ENV OLLAMA_HOST=0.0.0.0

# Start Ollama in the background, pull the models, then shut it down
RUN ollama serve & \
    sleep 5 && \
    ollama pull qwen3-embedding:0.6b

# Stage 2: Final Production Image
FROM ollama/ollama:0.20.7

# Financial institutions usually require a non-root user
# Note: Ollama's official image runs as root by default; 
# you may need to adjust permissions for /root/.ollama
COPY --from=downloader /root/.ollama /root/.ollama

# Performance Tuning for CPU (2026 specific optimizations)
# Enable AVX-512/AMX if your server hardware supports it
ENV OLLAMA_NUM_PARALLEL=4
ENV OLLAMA_MAX_LOADED_MODELS=1

EXPOSE 11434

ENTRYPOINT ["ollama", "serve"]