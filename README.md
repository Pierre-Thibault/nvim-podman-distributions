[![stars](https://img.shields.io/github/stars/Pierre-Thibault/nvim-podman-distributions)](https://github.com/Pierre-Thibault/nvim-podman-distributions)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

# nvim-podman-distributions

![image](https://github.com/user-attachments/assets/bb4fc0fe-5fd3-431f-9ad5-de65f207889d)


Ready to use scripts to start using a Neovim distribution using a Docker container.

## Description

Using Neovim on NixOS can be challenging because this Linux distribution does use the [Filesystem Hierarchy Standard (FHS)](https://www.geeksforgeeks.org/linux-file-hierarchy-structure/). And Neovim plugins tend to install binaries or libraries dependent upon the file hierarchy to link with their dependencies.

So, one alternative is using a temporary container with an interactive session. It is also a way to try a Neovim distribution live before a full traditional installation. Or, it can also be used as an alternative for working permanently.

Each folder in this project matches a Neovim distribution:

- [Astrovim](https://docs.astronvim.com/)
- [Lazyvim](https://www.lazyvim.org/)
- [NvChad](https://nvchad.com/)

There are only three at the moment. I hope people will do PRs to add more. Doing so is really to do.

This project is using both BASH and Podman. It should work on any POSIX system, and it probably works on Windows WSL too (I haven't tested, so please let me know.).

## Table of contents

```
$ tree .
.
├── AstroVim
│   ├── Dockerfile
│   └── run
├── LazyVim
│   ├── Dockerfile
│   └── run
├── LICENSE
└── NvChad
    ├── Dockerfile
    └── run

4 directories, 7 files
```
## How to use

### Requirements

- Bash
- Podman
- a terminal that supports true colour and undercurl, for example:

    - [kitty](https://github.com/kovidgoyal/kitty) (Linux & Macos)
    - [wezterm](https://github.com/wez/wezterm) (Linux, Macos & Windows)
    - [alacritty](https://github.com/alacritty/alacritty) (Linux, Macos & Windows)
    - [iterm2](https://iterm2.com/) (Macos)

### How to use

Just run one of the script, the corresponding `run` file of the distribution that you would like to try in a terminal. The script will then build the image and run it as an interactive session in a temporary container. You can pass the path of the directory or the file you would like to work as the first parameter. Otherwise, the default is the current directory. The directory, or the directory of the file, you passed will be mounted at `/root/project` in the container, so you can work on your project as if Neovim were running locally.

On the host `$HOME/.config/pt-nvim-podman-distributions`, the Neovim state will be preserved so you can customize your installation and keep your changes from session to session. As you progress, you may need to add dependencies in the `Dokerfile` based on the plugins you add. If so, just delete the corresponding docker image to force the `run` script to recreate it.

The first start will take a few minutes or the time to create the image and to download all the requirements. Subsequent starts are very fast because there is only a container to create.

#### Notes

NvChad gives some errors. It is recommended to first [configure LSPs](https://nvchad.com/docs/config/lsp) before starting working on language files.

## How to uninstall

1. Delete the corresponding Docker image `
   podman images -a; # List images
   podman rmi image-name # Delete the image named image-name`
3. Delete the corresponding directory in `$HOME/.config/pt-nvim-podman-distributions` `
   rm -rf $HOME/.config/pt-nvim-podman-distributions/image-name`

## How to contribute

To add a new Neovim distribution, the easiest way is probably to copy an existing one under another name. Then, there are mostly three changes to make:

1. In the Dockerfile, add or remove packages to install as needed.
2. In the script, change the value of IMAGE_NAME to match the name of your distribution.
3. In the script again, modify the `git clone` command for the one matching your distribution.

Create an issue on Github if needed. Feedback is welcome.

## License

[MIT License](https://mit-license.org/)
