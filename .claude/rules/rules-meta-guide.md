
- **Rule Format:**
  - Use clear markdown structure
  - Start with main points in bold
  - Include sub-points with details and examples
  - Provide specific, actionable guidance

- **File References:**
  - Reference files by their relative path from project root
  - Example: `.claude/rules/architecture-rules.md` for rule references

- **Code Examples:**
  - Use language-specific code blocks
  ```swift
  // ✅ DO: Show good examples
  struct GoodView: View {
      var body: some View { ... }
  }
  
  // ❌ DON'T: Show anti-patterns
  class BadViewController: UIViewController { ... }
  ```

- **Rule Content Guidelines:**
  - Start with high-level overview
  - Include specific, actionable requirements
  - Show examples of correct implementation
  - Reference existing code when possible
  - Keep rules DRY by referencing other rules

- **Rule Maintenance:**
  - Update rules when new patterns emerge
  - Add examples from actual codebase
  - Remove outdated patterns
  - Cross-reference related rules using relative paths

- **Best Practices:**
  - Use bullet points for clarity
  - Keep descriptions concise
  - Include both DO and DON'T examples
  - Reference actual code over theoretical examples
  - Use consistent formatting across rules
  - Focus on Swift/iOS specific patterns
  - Include architectural guidance for SwiftUI apps 