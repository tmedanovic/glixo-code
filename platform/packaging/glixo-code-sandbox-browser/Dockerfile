# Minimal Linux sandbox for browser container2wasm (experimental Glixo Code tryout).
# Full image: git, ripgrep, node/npm, bash, Vite starter — tag glixo-debian-c2w:<version>
FROM debian:bookworm-slim

RUN apt-get update && apt-get install -y --no-install-recommends \
    git \
    ripgrep \
    nodejs \
    npm \
    bash \
    curl \
    ca-certificates \
    coreutils \
    findutils \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /workspace
ENV PATH="/workspace/node_modules/.bin:${PATH}"

COPY starter/package*.json ./
RUN npm ci --no-audit --no-fund \
    && npm cache clean --force

COPY starter/ ./

# Default: interactive shell (c2w browser shell drives commands programmatically).
CMD ["/bin/bash"]
