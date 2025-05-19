# WSL Setup Guide

This guide provides step-by-step instructions for setting up a new Ubuntu WSL (Windows Subsystem for Linux) distribution.

## 1. Initial Setup

### Create Development Directories

```bash
mkdir -p dev/github/juanmherrerav dev/github/atomadvantage
```

### Install GitHub CLI

[Installation for Debian Based Distros and more](https://github.com/cli/cli/blob/trunk/docs/install_linux.md)

```bash
(type -p wget >/dev/null || (sudo apt update && sudo apt-get install wget -y)) \
    && sudo mkdir -p -m 755 /etc/apt/keyrings \
    && out=$(mktemp) && wget -nv -O$out https://cli.github.com/packages/githubcli-archive-keyring.gpg \
    && cat $out | sudo tee /etc/apt/keyrings/githubcli-archive-keyring.gpg > /dev/null \
    && sudo chmod go+r /etc/apt/keyrings/githubcli-archive-keyring.gpg \
    && echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null \
    && sudo apt update \
    && sudo apt install gh -y
```

### Configure GitHub Access

```bash
cd ~/dev/github/juanmherrerav
gh auth login  # Log into GitHub with personal account
```

## 2. Windows Development Tools

Install essential Windows development tools using winget:

```powershell
winget install -e --id Microsoft.VisualStudioCode
winget install -e --id=JanDeDobbeleer.OhMyPosh
winget install --id=DEVCOM.JetBrainsMonoNerdFont -e
oh-my-posh font install meslo
```

## 3. Python Development Environment

### Install Pyenv Build Dependencies

```bash
sudo apt-get install -y make build-essential libssl-dev zlib1g-dev \
libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev \
libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev python3-openssl
```
