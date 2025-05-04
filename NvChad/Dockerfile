# Utiliser l'image de base Alpine Linux
FROM alpine:latest

# Mettre à jour les paquets et installer les dépendances nécessaires
RUN apk update && \
    apk add --no-cache \
    bottom \
    build-base \
    cmake \
    curl \
    curl \
    fd \
    fzf \
    gettext-dev \
    git \
    go \
    lazygit \
    libtermkey \
    libvterm \
    lua \
    lua-dev \
    luarocks \
    ninja \
    nodejs \
    npm \
    python3 \
    ripgrep \
    ripgrep \
    unzip \
    wget

# Télécharger et compiler Neovim 0.11
RUN git clone --branch v0.11.0 https://github.com/neovim/neovim.git /tmp/neovim && \
    cd /tmp/neovim && \
    make CMAKE_BUILD_TYPE=Release && \
    make install && \
    rm -rf /tmp/neovim

# Nettoyer les paquets de build pour réduire la taille de l'image
RUN apk del ninja && \
    rm -rf /var/cache/apk/*

# Définir le répertoire de travail
WORKDIR /root

# Commande par défaut
ENTRYPOINT ["nvim"]
