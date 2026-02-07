# Purpose

A centralized collection of Cursor AI rules, Claude AI agents, commands, skills, and Apple framework documentation designed to enhance AI-assisted iOS/Swift development workflows. These resources provide clear context about coding standards, architectural decisions, and framework usage patterns to ensure consistent code quality across projects.

## Cursor

### 🏗️ Architecture & Design

- [**Forget MVVM (by Dimillian)**](cursor/rules/forget-mvvm-by-Dimillian.mdc) — Modern SwiftUI architecture patterns that embrace declarative UI and native data flow instead of legacy MVVM patterns.
- [**Modular Architecture**](cursor/rules/modular-architecture.mdc) — Guidelines for a modular Swift Package architecture with Core infrastructure and self-contained Features.

### 📋 Issue & Task Management

- [**GitHub Issue**](cursor/rules/gh-issue.mdc) — Create comprehensive GitHub issues with proper templates and CLI integration.
- [**ZenHub Issue**](cursor/rules/zh-issue.mdc) — Create comprehensive ZenHub issues with proper templates and MCP functions.

### 🔧 Development Workflow

- [**Commit Message**](cursor/rules/commit-message.mdc) — Conventional Commits guidelines with recommended tags and footer metadata.
- [**Commit Staged & Push**](cursor/rules/commit-staged-push.mdc) — Commit staged changes and push to remote.
- [**Pull Request**](cursor/rules/pr.mdc) — Pull request creation guidelines with GitHub CLI integration and emoji conventions.

### 🎨 Code Quality

- [**SwiftFormat**](cursor/rules/swiftformat.mdc) — Automatic code formatting with SwiftFormat for consistent Swift code style.

### ⚠️ Critical Rules

- [**Critical Rules — Never Violate**](cursor/rules/critical-rules-never-violate.mdc) — Critical workspace rules that must always be followed (e.g., never commit without explicit request).

### 📖 Meta

- [**Cursor Rules Meta Guide**](cursor/rules/cursor-rules-meta-guide.mdc) — Guidelines for creating and maintaining Cursor rules to ensure consistency and effectiveness.

## Claude

### 🤖 Agents

- [**QA Test Engineer**](claude/agents/qa-test-engineer.md) — Expert QA engineer for assessing test coverage, creating test strategies, writing test cases, and verifying application functionality.
- [**Security Audit Specialist**](claude/agents/security-audit-specialist.md) — Senior security auditor for credential management review, token handling, and architecture security assessment.
- [**SwiftUI Architect**](claude/agents/swiftui-architect.md) — SwiftUI architecture specialist for building clean, maintainable views using modern iOS 18/26 features and proper component patterns.

### 🛠️ Commands

- [**Commit Staged**](claude/commands/commit-staged.md) — Commit staged changes following project commit message guidelines.
- [**Document Core UI Components**](claude/commands/document-core-ui-components.md) — Generate a concise quick-reference for the Core package's DesignSystem, SharedUI, and Router modules.
- [**Extract to Package**](claude/commands/extract-it-to-package.md) — Extract requested functionality into a Swift Package with proper structure and public API.
- [**Pull Request**](claude/commands/pr.md) — Create or edit GitHub Pull Requests following project PR guidelines.
- [**Update README**](claude/commands/update.md) — Update the README.md with a structured summary of all rules and documentation.
- [**View Config**](claude/commands/view-config.md) — Refactor SwiftUI views into configurable components with nested ViewConfiguration struct and modifier functions.
- [**ZenHub Issue**](claude/commands/zh.md) — Create or update ZenHub issues following project workflows.

### 📐 Rules

- [**Build Commands**](claude/rules/build-commands.md) — XcodeBuildMCP tool usage for building, testing, and managing iOS projects.
- [**Commit Message**](claude/rules/commit-message.md) — Commit message conventions with issue number extraction from branch names and conventional commits.
- [**GitHub Issue**](claude/rules/gh-issue.md) — GitHub issue creation workflow with templates, CLI commands, and quality guidelines.
- [**Modular Architecture**](claude/rules/modular-architecture.md) — Modular Swift Package architecture with Core and Features package structure.
- [**PR Guide**](claude/rules/pr-guide.md) — Pull request creation workflow with analysis, syncing, description templates, and review guidelines.
- [**Rules Meta Guide**](claude/rules/rules-meta-guide.md) — Guidelines for creating and maintaining Claude rules with proper structure and examples.
- [**SwiftFormat**](claude/rules/swiftformat.md) — SwiftFormat integration requirements and best practices for automatic code formatting.
- [**SwiftUI Architecture**](claude/rules/swiftui-architecture.md) — UI-heavy feature architecture principles: native state management, no ViewModels, unidirectional data flow.
- [**SwiftUI View Organization**](claude/rules/swiftui-view-organization.md) — View structure conventions including property ordering, body decomposition, and extension-based helpers.
- [**Unit Testing**](claude/rules/unit-testing.md) — Unit testing guidelines using Swift Testing framework with decision framework and examples.
- [**ZenHub Issue**](claude/rules/zh-issue.md) — ZenHub issue creation workflow with MCP functions, templates, and pipeline configuration.

### 🧩 Skills

- [**Agent Rules Writer**](claude/skills/agent-rules-writer/SKILL.md) — Guide for writing and maintaining agent rules files with proper structure and DO/DON'T examples.
- [**Explaining Code**](claude/skills/explaining-code/SKILL.md) — Explains code with visual ASCII diagrams, analogies, and step-by-step walkthroughs.

## Documentation

### 📚 Apple Framework References

- [**AppKit Documentation**](docs/AppKit%20Documentation.md) — Comprehensive AppKit reference for building macOS graphical user interfaces (1,847 pages).
- [**Swift Concurrency**](docs/Swift%20Concurrency.md) — Complete guide to Swift 6 data race safety, actors, Sendable protocol, and strict concurrency.
- [**SwiftData Documentation**](docs/SwiftData%20Documentation.md) — SwiftData reference for declarative model persistence and efficient fetching (292 pages).
- [**SwiftUI Documentation**](docs/SwiftUI%20Documentation.md) — SwiftUI reference for declarative UI and behavior across all Apple platforms (1,982 pages).
- [**UIKit Documentation**](docs/UIKit%20Documentation.md) — UIKit reference for building iOS, iPadOS, and tvOS graphical user interfaces (1,935 pages).

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
