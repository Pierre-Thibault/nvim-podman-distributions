# Use the official NixOS base image
FROM nixos/nix:latest

# Set up Nix environment
RUN nix-channel --add https://nixos.org/channels/nixpkgs-unstable nixpkgs && \
    nix-channel --update

# Install Neovim (unstable) using nix-env
RUN nix-env -iA nixpkgs.gcc
RUN nix-env -iA nixpkgs.git
RUN nix-env -iA nixpkgs.gnumake
RUN nix-env -iA nixpkgs.neovim
RUN nix-env -iA nixpkgs.nodejs_23
RUN nix-env -iA nixpkgs.ripgrep
RUN nix-env -iA nixpkgs.wget

# Set the entrypoint to Neovim
ENTRYPOINT ["nvim"]
