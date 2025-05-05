# Use alpine:latest as the base image
FROM alpine:edge

# Set working directory to /root
WORKDIR /root

# Update package index and install required packages
RUN apk update && \
    apk add --no-cache \
        alpine-sdk \
        bash \
        curl \
        git \
        lazygit \
        make \
        neovim \
        npm \
        nodejs \
        cargo \
        ripgrep
