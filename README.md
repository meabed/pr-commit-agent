# GGPR - PR & Commit AI Assistant

GGPR is a smart CLI tool leveraging AI to enhance Git workflows by generating high-quality commit messages and pull requests. It helps developers maintain better documentation of code changes, follow best practices, and create more descriptive PRs with minimal effort.

[![NPM Version](https://img.shields.io/npm/v/pr-commit-ai-agent.svg)](https://www.npmjs.com/package/pr-commit-ai-agent)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![CI](https://github.com/meabed/pr-commit-ai-agent/actions/workflows/ci.yml/badge.svg)](https://github.com/meabed/pr-commit-ai-agent/actions/workflows/ci.yml)

<div align="center">
  <img src="https://raw.githubusercontent.com/meabed/pr-commit-ai-agent/main/assets/demo.gif" alt="GGPR Demo" width="800"/>
</div>

## 🚀 Features

- **AI-Generated Commit Messages** - Create semantic commits that follow best practices
- **Commit Message Optimization** - Improve existing messages with AI suggestions
- **Smart Branch Names** - Generate descriptive branch names based on your changes
- **Automated PR Creation** - Generate PR titles, descriptions, and create them automatically
- **Multiple LLM Support** - Choose from OpenAI, Anthropic, Ollama, or DeepSeek
- **Local AI Integration** - Use with local models through Ollama for privacy
- **Customizable Workflows** - Configure prompts and behavior to match your team's practices
- **GitHub CLI Integration** - Seamless creation of PRs via GitHub CLI when available

## 📋 Requirements

- **Node.js** v18+
- **pnpm** (recommended) or npm
- **Git** v2.25+
- **GitHub CLI** (required) for PR creation

## 🛠️ Installation

### Global Installation (for users)

```bash
# Install globally with npm
npm install -g pr-commit-ai-agent

# Or with pnpm (recommended)
pnpm add -g pr-commit-ai-agent
```

### Development Installation (for contributors)

```bash
# Clone the repository
git clone https://github.com/meabed/pr-commit-ai-agent.git
cd pr-commit-ai-agent

# Install dependencies
pnpm install

# Link the package globally
pnpm link --global
```

## ⚙️ Configuration

### Option 1: Interactive Configuration (Recommended)

```bash
# Run the interactive configuration wizard
ggpr config
```

### Option 2: Environment Variables

```bash
# Set for current session
export LLM_PROVIDER=openai
export OPENAI_API_KEY=your_key_here

# Or pass inline for a single command
LLM_PROVIDER=ollama MODEL=qwen2.5-coder OLLAMA_BASE_URL=http://0.0.0.0:11434/api/generate ggpr
```

### Option 3: Configuration File

- run `ggpr config` to find the config file location, for example (`~/.config/pr-commit-ai-agent-nodejs/config.json`)
- modify the config file to set your preferred settings

### Available Environment Variables

| Environment Variable | Description                                                      | Default                      |
| -------------------- | ---------------------------------------------------------------- | ---------------------------- |
| `LLM_PROVIDER`       | AI provider to use (`openai`, `anthropic`, `ollama`, `deepseek`) | `openai`                     |
| `OPENAI_API_KEY`     | OpenAI API key                                                   | -                            |
| `ANTHROPIC_API_KEY`  | Anthropic API key                                                | -                            |
| `DEEPSEEK_API_KEY`   | DeepSeek API key                                                 | -                            |
| `OLLAMA_BASE_URL`    | URL for Ollama API                                               | `http://localhost:11434/api` |
| `OLLAMA_API_KEY`     | API key for Ollama (if needed)                                   | -                            |
| `MODEL`              | Override default model for selected provider                     | Provider-specific            |

## 📝 Usage

### Create Command (Default)

Guides you through creating AI-enhanced commits, optimizing messages, and creating a PR.

```bash
# Basic usage (interactive)
ggpr

# Or just:
ggpr create

# Auto-confirm all prompts
ggpr --yes

# Log all LLM requests for debugging
ggpr --log-request

# Combine flags
ggpr --yes --log-request

# PR creation
ggpr --pr
```

### Info Command

Shows repository information and status.

```bash
ggpr info

# Show detailed information
ggpr info --full
```

### Config Command

Manage your GGPR configuration settings.

```bash
# View and modify current config
ggpr config
```

## 📚 Command Reference

### Create Command (default)

The `create` command is the primary command for generating AI-enhanced commits and pull requests. It guides you through the process of creating commit messages, optimizing them, and generating pull requests.

#### Usage

```bash
ggpr
# or
ggpr create
```

#### Options

| Flag            | Alias | Description                                                       |
| --------------- | ----- | ----------------------------------------------------------------- |
| `--yes`         | `-y`  | Auto-confirm all prompts                                          |
| `--log-request` | `-l`  | Log LLM API requests for debugging                                |
| `--pr`          |       | Generate commit description and commit and branch and create a PR |

---

### Config Command

The `config` command allows you to view and modify the configuration settings for GGPR. You can use it interactively or modify the configuration file directly.

#### Usage

```bash
ggpr config
```

#### Options

| Flag     | Alias | Description           |
| -------- | ----- | --------------------- |
| `--help` | `-h`  | Show help information |

---

### Logs Command

The `logs` command provides access to the logs of previous LLM requests and responses. This is useful for debugging or reviewing past interactions.

#### Usage

```bash
ggpr logs
```

#### Options

| Flag     | Alias | Description           |
| -------- | ----- | --------------------- |
| `--help` | `-h`  | Show help information |

---

### Info Command

The `info` command displays information about the current repository, including its status and configuration.

#### Usage

```bash
ggpr info
```

#### Options

| Flag     | Alias | Description               |
| -------- | ----- | ------------------------- |
| `--full` |       | Show detailed information |
| `--help` | `-h`  | Show help information     |

---

### Common Options

These flags are available for most commands:

| Flag        | Alias | Description              |
| ----------- | ----- | ------------------------ |
| `--help`    | `-h`  | Show help information    |
| `--version` | `-v`  | Show version information |

## 🚶 Workflow

The `create` command workflow:

1. **Target Branch Selection** - Choose which branch to target for your PR
2. **Uncommitted Changes** - Generate an AI commit message for your changes
3. **Commit Optimization** - AI improves your existing commit messages
4. **Branch Creation** - Creates a branch with an AI-generated name if needed
5. **PR Creation** - Creates a PR with AI-generated title and description

## 🛠️ Development

### Quick Start for Contributors

```bash
# Clone and setup
git clone https://github.com/meabed/pr-commit-ai-agent.git
cd pr-commit-ai-agent
pnpm install

# Development mode
pnpm start create

# Testing
pnpm test

# Build
pnpm build
```

### Available Scripts

| Command            | Description                                 |
| ------------------ | ------------------------------------------- |
| `pnpm build`       | Build the project using tsup                |
| `pnpm build:watch` | Build with file watching                    |
| `pnpm start [cmd]` | Run the CLI using ts-node                   |
| `pnpm commit`      | Use commitizen for standard commit messages |
| `pnpm format`      | Check code formatting                       |
| `pnpm format:fix`  | Fix code formatting issues                  |
| `pnpm lint`        | Check for code style issues                 |
| `pnpm lint:fix`    | Fix code style issues                       |
| `pnpm test`        | Run unit tests                              |
| `pnpm release`     | Create a new release                        |

## 🤝 Contributing

We welcome contributions of all sizes! Here's how you can help:

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](./LICENSE) file for details.

---

<div align="center">
  <p>Made with ❤️ by <a href="https://github.com/meabed">Mohamed Meabed</a> and contributors</p>
  <p>
    <a href="https://github.com/meabed/pr-commit-ai-agent/stargazers">⭐ Star us on GitHub</a> •
    <a href="https://github.com/meabed/pr-commit-ai-agent/issues">🐛 Report Bug</a> •
    <a href="https://github.com/meabed/pr-commit-ai-agent/issues">✨ Request Feature</a>
  </p>
</div>
