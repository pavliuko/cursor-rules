# Cursor Rules & Documentation Repository

This repository contains a comprehensive collection of Cursor AI rules, Claude AI agents and instructions, architectural guidelines, and Apple framework documentation to enhance development workflows and ensure consistent code quality across projects.

## Purpose

This collection serves as a centralized knowledge base for:
- **Cursor AI Rules**: Context-aware guidelines that help AI assistants understand project conventions and best practices
- **Claude AI Agents**: Specialized AI personas for specific development tasks (QA testing, security audits, SwiftUI architecture)
- **Claude Commands & Rules**: Workflow automation and development guidelines for Claude Code
- **Apple Framework Documentation**: Comprehensive references for SwiftUI, UIKit, AppKit, SwiftData, and Swift Concurrency
- **Development Guidelines**: Architecture patterns, commit conventions, issue templates, and code formatting standards

These resources enable more effective AI-assisted development by providing clear context about coding standards, architectural decisions, and framework usage patterns.

## Cursor Rules

### 🏗️ Architecture & Design

- **[forget-mvvm-by-Dimillian](.cursor/rules/forget-mvvm-by-Dimillian.mdc)** - Modern SwiftUI architecture patterns that embrace declarative UI and native data flow instead of legacy MVVM patterns
- **[modular-architecture](.cursor/rules/modular-architecture.mdc)** - Guidelines for transitioning to a modular Swift Package architecture with clear separation between Core infrastructure and Features

### 📋 Issue & Task Management

- **[gh-issue](.cursor/rules/gh-issue.mdc)** - Create comprehensive GitHub issues with proper templates and CLI integration
- **[zh-issue](.cursor/rules/zh-issue.mdc)** - Create comprehensive ZenHub issues with proper templates

### 🔧 Development Workflow

- **[commit-message](.cursor/rules/commit-message.mdc)** - Use this rule to create git commit message
- **[commit-staged-push](.cursor/rules/commit-staged-push.mdc)** - Commit staged changes and push
- **[pr](.cursor/rules/pr.mdc)** - Pull request creation guidelines with GitHub CLI integration

### 🎨 Code Quality

- **[swiftformat](.cursor/rules/swiftformat.mdc)** - Automatic code formatting with SwiftFormat for consistent Swift code style

### ⚠️ Critical Rules

- **[critical-rules-never-violate](.cursor/rules/critical-rules-never-violate.mdc)** - Critical workspace rules. Must always follow.

### 📖 Meta & Documentation

- **[cursor-rules-meta-guide](.cursor/rules/cursor-rules-meta-guide.mdc)** - Guidelines for creating and maintaining Cursor rules to ensure consistency and effectiveness

## Claude AI Configuration

### 🤖 Specialized Agents

- **[qa-test-engineer](.claude/agents/qa-test-engineer.md)** - Expert QA engineer for assessing test coverage, creating test strategies, writing test cases, and verifying application functionality
- **[security-audit-specialist](.claude/agents/security-audit-specialist.md)** - Senior security auditor for comprehensive security audits, credential management review, and architecture security assessment
- **[swiftui-architect](.claude/agents/swiftui-architect.md)** - SwiftUI architecture specialist for building clean, maintainable views using modern iOS 18/26 features and proper component patterns

### 📝 Claude Commands

- **[commit-staged](.claude/commands/commit-staged.md)** - Commit staged changes following project commit message guidelines
- **[extract-it-to-package](.claude/commands/extract-it-to-package.md)** - Extract requested functionality into a Swift Package with proper structure and public API
- **[pr](.claude/commands/pr.md)** - Create or edit GitHub Pull Requests following project PR guidelines
- **[view-config](.claude/commands/view-config.md)** - Refactor SwiftUI views into configurable components with ViewConfiguration struct and modifier functions
- **[zh](.claude/commands/zh.md)** - Create or update ZenHub issues following project workflows

### 📐 Claude Rules

- **[commit-message](.claude/rules/commit-message.md)** - Commit message conventions with issue number formatting and conventional commits
- **[gh-issue](.claude/rules/gh-issue.md)** - GitHub issue creation workflow with templates and CLI integration
- **[pr-guide](.claude/rules/pr-guide.md)** - Pull request creation workflow with analysis, syncing, and review guidelines
- **[rules-meta-guide](.claude/rules/rules-meta-guide.md)** - Guidelines for creating and maintaining Claude rules with proper structure and examples
- **[swiftformat](.claude/rules/swiftformat.md)** - SwiftFormat integration requirements and best practices
- **[zh-issue](.claude/rules/zh-issue.md)** - ZenHub issue creation workflow with MCP functions and templates

## Documentation

### 📚 Apple Framework References

- **[AppKit Documentation](docs/AppKit%20Documentation.md)** - Construct and manage a graphical, event-driven user interface for your macOS app (1,847 pages)
- **[Swift Concurrency](docs/Swift%20Concurrency.md)** - Complete guide to Swift 6 data race safety, actors, Sendable protocol, and strict concurrency migration
- **[SwiftData Documentation](docs/SwiftData%20Documentation.md)** - Write your model code declaratively to add managed persistence and efficient model fetching (292 pages)
- **[SwiftUI Documentation](docs/SwiftUI%20Documentation.md)** - Declare the user interface and behavior for your app on every platform (1,982 pages)
- **[UIKit Documentation](docs/UIKit%20Documentation.md)** - Construct and manage a graphical, event-driven user interface for your iOS, iPadOS, or tvOS app (1,935 pages)

## Commands

### 📝 Cursor Commands

- **[update](.cursor/commands/update.md)** - Update the README.md file with an up-to-date, structured summary of all rules and documentation

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

---

*Last updated: October 6, 2025*
