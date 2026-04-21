# Stage 1: Model downloader
FROM --platform=linux/amd64 ollama/ollama:0.21.0 AS downloader

# Start Ollama in the background, pull the models, then shut it down
# We pull to the default /root/.ollama location in this stage
RUN ollama serve & \
    sleep 5 && \
    ollama pull gpt-oss:20b

# Stage 2: Final Production Image
FROM ollama/ollama:0.21.0

# Create a non-root user for security best practices
RUN useradd -m -u 2000 ollamauser

# Set environment variables for the new user's home
# This tells Ollama where to look for manifests and blobs
ENV OLLAMA_MODELS=/home/ollamauser/.ollama/models
RUN mkdir -p $OLLAMA_MODELS && chown -R ollamauser:ollamauser /home/ollamauser

# Copy model files from the downloader stage
# We use --chown to ensure the files are owned by our non-root user immediately.
# We copy from /root/.ollama/models specifically to maintain the correct internal folder structure.
COPY --from=downloader --chown=ollamauser:ollamauser /root/.ollama/models /home/ollamauser/.ollama/models

# Assume the non-root user
USER ollamauser

# Performance Tuning for CPU (2026 specific optimizations)
ENV OLLAMA_NUM_PARALLEL=4
ENV OLLAMA_MAX_LOADED_MODELS=1
ENV OLLAMA_HOST=0.0.0.0

EXPOSE 11434

ENTRYPOINT ["/bin/ollama", "serve"]
