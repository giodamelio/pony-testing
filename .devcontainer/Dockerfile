# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.203.0/containers/ubuntu/.devcontainer/base.Dockerfile

# [Choice] Ubuntu version (use hirsuite or bionic on local arm64/Apple Silicon): hirsute, focal, bionic
ARG VARIANT="hirsute"
FROM mcr.microsoft.com/vscode/devcontainers/base:0-${VARIANT}

RUN apt-get update \
 && apt-get install -y --no-install-recommends \
    ca-certificates \
    clang \
    curl \
    g++ \
    git \
    make \
  && rm -rf /var/lib/apt/lists/*

USER vscode

ENV PATH "/home/vscode/.local/share/ponyup/bin:$PATH"

RUN sh -c "$(curl --proto '=https' --tlsv1.2 -sSf https://raw.githubusercontent.com/ponylang/ponyup/latest-release/ponyup-init.sh)" \
 && ponyup update ponyc release \
 && ponyup update stable release \
 && ponyup update corral release \
 && ponyup update changelog-tool release