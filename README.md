# Quarto Codespaces

[![Dev Container Docker Image Build](https://github.com/mcanouil/quarto-codespaces/actions/workflows/devcontainer.yml/badge.svg?event=release)](https://github.com/mcanouil/quarto-codespaces/actions/workflows/devcontainer.yml)

Setup to deploy [GitHub Codespaces](https://github.com/features/codespaces) (Codespaces) or [Development Containers](https://containers.dev/) (Dev Containers) with [Quarto](https://quarto.org/).

## Overview

This repository provides a setup to deploy Codespaces or Dev Containers with Quarto, supporting R, Python, and Julia environments.
It includes configuration files and scripts to initialise and manage these environments.

Using [`ghcr.io/mcanouil/quarto-codespaces:latest`](https://github.com/mcanouil/quarto-codespaces/pkgs/container/quarto-codespaces) as a base image for a quick deployment (Ubuntu 22.04 - Jammy Jellyfish):  
[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/mcanouil/quarto-codespaces?quickstart=1&devcontainer_path=.devcontainer%2Fdevcontainer.json)

Using Codespaces default base image ([`ghcr.io/mcanouil/quarto-codespaces:release-universal`](https://github.com/mcanouil/quarto-codespaces/pkgs/container/quarto-codespaces)) to mitigate GitHub storage usage (Ubuntu 20.04 - Focal Fossa):  
[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/mcanouil/quarto-codespaces?quickstart=1&devcontainer_path=.devcontainer%2Funiversal%2Fdevcontainer.json)

## Using as a Template

You can use this repository as a template for your own projects.
To do so, click the "Use this template" button on the GitHub repository page.
This will create a new repository with the same files and structure.

## Using with Codespaces

This repository is configured to work with GitHub Codespaces.
To use it, follow these steps:

1. Open the repository on GitHub.
2. Click the "Code" button and select "Open with Codespaces".
3. If you don't have a Codespace already, create a new one.
4. The Codespace will be set up automatically using the configuration provided in this repository.

## Dev Container Configuration

The Dev Container configuration is located in [`.github/.devcontainer/devcontainer.json`](.github/.devcontainer/devcontainer.json).
This file defines the development container settings, including the base image, user settings, and features to be installed.

### Key Features

- **Base Image**: The container uses the `buildpack-deps:jammy-curl` image as the base.
- **Remote User**: The default user is set to `vscode`.
- **Installed Features**:
  - Common utilities with Zsh shell.
  - [Git](https://git-scm.com/) for version control.
  - [R](https://www.r-project.org/) with `renv` support and `rmarkdown`.
  - [Python](https://www.python.org/) with shared libraries, `jupyter` and [`uv`](https://docs.astral.sh/uv/).
  - [Julia](https://julialang.org/) with the latest release channel and `IJulia`.
  - [TinyTeX](https://github.com/rstudio/tinytex) for LaTeX support.
  - [Decktape](https://github.com/astefanutti/decktape) for PDF generation from HTML presentations.
  - [Quarto CLI](https://quarto.org/) for scientific and technical publishing.

### Docker Image

The Dev Container configuration is used to build a Docker image that is available for use.
You can pull the latest image (using Quarto stable release) using the following command:

```sh
docker pull ghcr.io/mcanouil/quarto-codespaces:latest
```

Available tags: [`ghcr.io/mcanouil/quarto-codespaces`](https://github.com/mcanouil/quarto-codespaces/pkgs/container/quarto-codespaces)

## Initialisation Script

The initialisation script [init.sh](init.sh) is used to set up the R, Python, and Julia environments.
It supports initialising all environments or specific ones based on the provided options.

### Usage

```sh
./init-env.sh [--what/-w all|r|python|julia] [--force/-f] [--help/-h]
```

### Script Details

- **Options**:
  - `--what/-w`: Specify which environment(s) to initialise (`all`, `r`, `python` (uv), `julia`).
  - `--force/-f`: Force reinstallation of the specified environment(s).
  - `--help/-h`: Display help message and exit.
- **Functionality**: The script installs necessary dependencies for R, Python, and Julia, inside environments.
  - For R, it sets up `renv` and installs required packages.
  - For Python, it sets up uv and installs required libraries.
  - For Julia, it sets up an environment and installs required packages.

## Contributing

Contributions are welcome!
Please open an issue or submit a pull request for any improvements or bug fixes.

## License

This project is licensed under the MIT License.
See the [LICENSE](LICENSE) file for details.
