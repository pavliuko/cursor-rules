# Purpose

This repository contains a comprehensive collection of Cursor rules, Claude instructions, and Apple platform documentation designed to enhance development workflows for iOS, macOS, and SwiftUI projects. The rule set emphasizes modern SwiftUI architecture patterns, automated tooling, and best practices for creating maintainable code while providing extensive documentation for Apple's frameworks.

## Cursor

### 🛠️ Development Workflow
- [**commit-message**](.cursor/rules/commit-message.mdc) - Use this rule to create git commit message
- [**commit-staged-push**](.cursor/rules/commit-staged-push.mdc) - Commit staged changes and push
- [**pr**](.cursor/rules/pr.mdc) - Pull request creation guidelines

### 🏗️ Architecture & Patterns  
- [**forget-mvvm-by-Dimillian**](.cursor/rules/forget-mvvm-by-Dimillian.mdc) - SwiftUI 2025 Architecture Rules (always applied)

### 📋 Issue Management
- [**gh-issue**](.cursor/rules/gh-issue.mdc) - Create comprehensive GitHub issues with proper templates and CLI integration
- [**zh-issue**](.cursor/rules/zh-issue.mdc) - Create comprehensive ZenHub(zh) issues with proper templates

### ⚙️ Maintenance
- [**update**](.cursor/rules/update.mdc) - Generate and update the README.md file with an up-to-date, structured summary

## Claude

### 💻 Commands
- [**commit-staged**](.claude/commands/commit-staged.md) - Commit staged changes following guidelines
- [**extract-it-to-package**](.claude/commands/extract-it-to-package.md) - Extract code components to Swift packages
- [**pr**](.claude/commands/pr.md) - Create pull requests using GitHub CLI
- [**view-config**](.claude/commands/view-config.md) - View and manage project configuration
- [**zh**](.claude/commands/zh.md) - ZenHub command utilities

### 👥 Agents
- [**qa-test-engineer**](.claude/agents/qa-test-engineer.md) - QA testing specialist agent
- [**security-audit-specialist**](.claude/agents/security-audit-specialist.md) - Security audit and vulnerability assessment agent
- [**swiftui-architect**](.claude/agents/swiftui-architect.md) - SwiftUI architecture and modern iOS development specialist

### 📋 Rules
- [**commit-message**](.claude/rules/commit-message.md) - Git commit message standards and conventions
- [**gh-issue**](.claude/rules/gh-issue.md) - GitHub issue creation templates and workflows
- [**pr-guide**](.claude/rules/pr-guide.md) - Pull request guidelines and best practices
- [**rules-meta-guide**](.claude/rules/rules-meta-guide.md) - Meta-guide for creating and managing rules
- [**swiftformat**](.claude/rules/swiftformat.md) - Code formatting standards using SwiftFormat
- [**zh-issue**](.claude/rules/zh-issue.md) - ZenHub issue management templates and processes

## Documentation

### 📱 Apple Frameworks
- [**AppKit Documentation**](docs/AppKit%20Documentation.md) - Comprehensive AppKit framework documentation for macOS development
- [**Swift Concurrency**](docs/Swift%20Concurrency.md) - Swift concurrency patterns, async/await, and structured concurrency
- [**SwiftData Documentation**](docs/SwiftData%20Documentation.md) - SwiftData framework documentation for data persistence
- [**SwiftUI Documentation**](docs/SwiftUI%20Documentation.md) - Complete SwiftUI framework documentation and API reference
- [**UIKit Documentation**](docs/UIKit%20Documentation.md) - UIKit framework documentation for iOS development

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.