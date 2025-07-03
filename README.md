# Claude Code Snippets 🤖

> **Supercharge your Claude Code workflows with battle-tested command snippets and development patterns**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude Compatible](https://img.shields.io/badge/Claude%20Code-Compatible-blue.svg)](https://claude.ai/code)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)

A curated collection of powerful command snippets that transform how you work with Claude Code. These snippets establish clear patterns, workflows, and guardrails to help you write better code faster while maintaining high quality standards.

## 🎯 Why Use These Snippets?

- **🛡️ Production-Ready**: Battle-tested patterns for production codebases
- **⚡ Efficiency Boost**: Streamline repetitive workflows and enforce best practices
- **🎮 Full Control**: Choose your level of autonomy from guided approval to full TDD
- **🔍 Quality First**: Built-in code review and quality checks
- **📚 Best Practices**: Follows KISS, YAGNI, and DRY principles out of the box

## 🪝 Hooks - Automated Workflows

Claude Code hooks allow you to automate repetitive tasks and enforce standards. Configure them in your `.claude/settings.json` file.

### Available Hooks

- **🎨 `auto-prettier`** - Automatically format code after every edit

### How to Install Hooks

1. Create a `.claude` directory in your project root (if not exists)
2. Create or edit `.claude/settings.json`
3. Copy the hook configuration from the desired hook file
4. Save and restart Claude Code

Example `.claude/settings.json`:
```json
{
  "hooks": {
    "PostToolUse": [
      // Your hooks here
    ]
  }
}
```

See the `hooks/` directory for detailed configurations and examples.

## 📋 Available Commands

### 🔒 `/approval-mode` - Controlled Development Workflow

**The perfect companion to Claude's Plan Mode** - while Plan Mode helps you strategize, Approval Mode gives you granular control over the actual implementation.

#### How it Works with Plan Mode

1. **Plan Mode**: Claude creates a high-level implementation strategy
2. **Approval Mode**: Takes that plan and breaks it into controlled, reviewable steps
3. **You Stay in Control**: Guide the implementation, correct course when needed

#### Key Features

- ✅ **Step-by-Step Control**: Review each implementation chunk before execution
- 📝 **Detailed Previews**: See exactly what will change before it happens
- 🔄 **Course Correction**: Redirect Claude if implementation drifts from intent
- 🛡️ **Safety First**: Prevent unintended modifications to critical code
- 🎯 **Thoughtful Implementation**: Uses sequential thinking for each major step

#### What Requires Approval

- Creating/deleting files or folders
- Installing packages or dependencies
- Major refactoring (>20 lines)
- Git operations
- Database changes
- Each feature implementation chunk

**Use when:** After planning phase, working on production code, implementing complex features, or when you need to ensure implementation matches your exact requirements

### 🔍 `/review` - Comprehensive Code Review

Get professional-grade code reviews with focus on:

- 🔐 Security vulnerabilities and best practices
- 🏗️ Architecture and design patterns
- 📊 Performance optimization opportunities
- 🧹 Code quality and maintainability
- 📖 Documentation completeness

**Use when:** Before merging PRs, after major features, or for code audits

### 🧪 `/tdd` - Pure Test-Driven Development

Enforces strict TDD with the classic Red-Green-Refactor cycle:

- 🔴 **Red**: Write failing tests first
- 🟢 **Green**: Implement minimal code to pass
- 🔄 **Refactor**: Improve code while tests stay green
- 🚫 No implementation without tests

**Use when:** Building new features, ensuring high test coverage, or learning TDD

## 📁 Repository Structure

```text
claude-code-snippets/
├── commands/
│   ├── approval-mode.md    # Controlled development workflow
│   ├── review.md          # Code review command
│   └── tdd.md            # Test-driven development
├── claudefiles/
│   └── CLAUDE_USER.md    # Global development principles
├── hooks/
│   └── auto-prettier.md   # Auto-format code after edits
└── README.md            # This file
```

### 💡 Special Files

- **`CLAUDE_USER.md`**: Core development principles including:
  - **KISS, YAGNI, DRY** principles for maintainable code
  - **Testing Philosophy**: Behavior-focused testing, no implementation details
  - **Communication Guidelines**: Clear, proactive communication
  - **Over-engineering Prevention**: Red flags and best practices

## 🚀 Getting Started

### Quick Start (Single Use)

1. Browse the `commands/` directory
2. Copy the content of your desired command
3. Paste it in your Claude Code conversation
4. Start with the command, e.g., `/approval-mode`

### Global Configuration (Recommended)

For consistent development practices across all projects:

```bash
# Create Claude configuration directory
mkdir -p ~/.claude

# Copy global principles
cp claudefiles/CLAUDE_USER.md ~/.claude/CLAUDE.md
```

Now these principles apply to all your Claude Code sessions!

## 📚 Command Examples

### Using Approval Mode

```text
User: /approval-mode
Claude: Approval mode activated. I'll request your approval before making changes.

User: Add error handling to the payment processor
Claude: I'll add error handling. Here's my plan:
1. Add try-catch blocks around payment API calls
2. Implement retry logic for transient failures
3. Add proper error logging

Shall I proceed with these changes? [yes/no]
```

### Running Code Review

```text
User: /review
Claude: I'll perform a comprehensive code review. Starting analysis...

[Reviews code for security, performance, maintainability, etc.]
```

## 🤝 Contributing

We welcome contributions! Here's how you can help:

1. **🐛 Report Issues**: Found a bug or have a suggestion? [Open an issue](https://github.com/yourusername/claude-code-snippets/issues)
2. **💡 Share Snippets**: Have a useful workflow? Submit a PR!
3. **📝 Improve Docs**: Help us make the documentation even better
4. **⭐ Star & Share**: If you find this helpful, star the repo and share with others

### Contribution Guidelines

- Follow the existing format for new commands
- Test your snippets thoroughly
- Include clear use cases and examples
- Keep commands focused on a single workflow

## 🎉 Success Stories

> "The approval mode snippet saved our production database from an accidental migration. Can't imagine working without it!" - *Senior Developer*
>
> "TDD mode helped our team increase test coverage from 40% to 85% in just two sprints." - *Tech Lead*

## 📄 License

MIT License - Use these snippets freely in your projects and share with your team!

---

Made with ❤️ by developers, for developers  
[⭐ Star us on GitHub](https://github.com/yourusername/claude-code-snippets)
