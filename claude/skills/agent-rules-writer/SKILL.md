---
name: agent-rules-writer
description: Guide for writing and maintaining agent rules files in CLAUDE.md and agent-rules/ directories. Use when creating new agent rules, updating existing rules, documenting coding conventions, or establishing project guidelines for AI agents. Triggers on requests like "create a rule for X", "add guidelines for Y", "document the pattern for Z", or when maintaining agent-rules/*.md files.
---

# Agent Rules Writer

Create and maintain agent rules that provide clear, actionable guidance for AI agents working in a codebase.

## Rule Structure

### Format
- Use clear markdown structure with headers
- Start main points in **bold**
- Include sub-points with details and examples
- Provide specific, actionable guidance

### File References
Reference files by relative path from project root:
```markdown
See `agent-rules/architecture-rules.md` for details.
```

## Code Examples

Always use language-specific code blocks with DO/DON'T patterns:

```swift
// ✅ DO: Show good examples
struct GoodView: View {
    var body: some View { ... }
}

// ❌ DON'T: Show anti-patterns
class BadViewController: UIViewController { ... }
```

## Content Guidelines

1. Start with high-level overview
2. Include specific, actionable requirements
3. Show examples of correct implementation
4. Reference existing code when possible
5. Keep rules DRY by referencing other rules

## Maintenance

- Update rules when new patterns emerge
- Add examples from actual codebase
- Remove outdated patterns
- Cross-reference related rules using relative paths

## Best Practices

- Use bullet points for clarity
- Keep descriptions concise
- Include both DO and DON'T examples
- Reference actual code over theoretical examples
- Use consistent formatting across rules
- Focus on domain-specific patterns (e.g., Swift/iOS for iOS projects)
- Include architectural guidance where relevant
