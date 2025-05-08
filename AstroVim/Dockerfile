# Use alpine:latest as the base image
FROM alpine:latest

# Set working directory to /root
WORKDIR /root

# Update package index and install required packages
RUN apk update && \
    apk add --no-cache git nodejs npm neovim ripgrep build-base wget lazygit curl fzf ripgrep fd go bottom python3

RUN npm install tree-sitter-cli

# Create the directory for the pointing point of the host
RUN mkdir /home/Project

# Set the entrypoint to wait an interactive session
ENTRYPOINT ["nvim"]
