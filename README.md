# Claude Code Snippets 🤖

A collection of powerful command snippets and workflows for Claude Code to supercharge your development process. These snippets help you work more efficiently with Claude by establishing clear patterns, workflows, and guardrails.

## 📋 Available Commands

### `/approval-mode` - Controlled Development Workflow

Activates a controlled development mode where Claude requests approval before making major changes. Perfect for production code or when you want to maintain tight control over the development process.

### `/review` - Comprehensive Code Review

Performs thorough, professional code reviews across repositories with focus on security, architecture, and code quality.

### `/tdd` - Pure Test-Driven Development

Enforces strict Test-Driven Development practices with the classic Red-Green-Refactor cycle.

## 📁 Directory Structure

### `@claudefiles/` Directory
This directory contains Claude-specific configuration files and user guidelines:

- **`CLAUDE_USER.md`** - Global development principles and coding guidelines that help maintain consistent, high-quality code across all projects. These principles emphasize simplicity, maintainability, and clear communication.

## 🚀 How to Use

1. Copy the content from any command file in the `.claude/commands` directory
2. run with e.g. `/approval-mode`
3. For global settings, place `CLAUDE_USER.md` content in your `~/.claude/CLAUDE.md` file
4. Enjoy enhanced development workflows!

## 🤝 Contributing

Found these snippets helpful? Star the repo and watch for updates! Have ideas for new snippets? Feel free to open an issue or submit a pull request.

## 📄 License

MIT License - feel free to use these snippets in your own projects and share with your team.
