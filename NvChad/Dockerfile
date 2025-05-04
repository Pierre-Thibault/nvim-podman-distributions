# Use alpine:latest as the base image
FROM alpine:latest

# Set working directory to /root
WORKDIR /root

# Update package index and install required packages
RUN apk update && \
    apk add --no-cache git nodejs neovim ripgrep build-base wget lua-language-server

# Clone NvChad starter configuration into ~/.config/nvim
RUN git clone https://github.com/NvChad/starter ~/.config/nvim

# Set the entrypoint to run Neovim
ENTRYPOINT ["nvim"]

