# GitHub Issue Creation Guidelines

## **Purpose**

When a user requests creating a GitHub issue, extract relevant details, determine the appropriate issue type, and generate a properly formatted issue with GitHub CLI command for the <github-repo-name> project.

## **Repository Configuration**

- **Target Repository:** `https://github.com/<github-org-name>/<github-repo-name>`
- **CLI Command Prefix:** `gh issue create --repo <github-org-name>/<github-repo-name>`

## **Issue Type Detection**

Automatically determine issue type based on user input:

- **🐛 Bug Report** - Problems, errors, crashes, unexpected behavior
- **✨ Feature Request** - New functionality, enhancements, user stories
- **📋 Task** - Development tasks, refactoring, technical debt

## **Issue Templates**

### **Bug Report Template**

```markdown
## 🐛 Problem

*Clear description of what's broken or not working as expected.*

## 📱 Environment

- **iOS Version:** 
- **Device Model:** 
- **App Version:** 
- **Xcode Version:** (if applicable)

## 🔄 Steps to Reproduce

1. 
2. 
3. 

## ✅ Expected Behavior

*Describe the correct or intended behavior.*

## 📸 Visual Evidence

*Attach screenshots, videos, or logs if relevant.*

## 🧩 Additional Context

*Include any other relevant details such as logs, edge cases, or linked issues.*
```

### **Feature Request Template**

```markdown
## ✨ Feature Overview

*Short description of the proposed feature or enhancement.*

## 🎯 Problem Addressed

*Summary of the need or issue this feature solves.*

## 💡 Proposed Solution

*High-level explanation of how the feature should work.*

## 👤 User Story

*As a [user type], want to [action] so that [benefit].*

## ✅ Acceptance Criteria

*Outcomes that define the feature as complete:*

- 
- 
- 

## 🔗 Related Issues

*Link any related tasks, issues, or discussions.*

## 📎 Supporting Material

*Include mockups, examples, or references if available.*
```

### **Task Template**

```markdown
## 📝 Summary

*Brief description of the task and its objective.*

## ✅ Acceptance Criteria

*List of conditions that determine task completion:*

- Aligned with user or business goals
- Broad enough to allow for implementation flexibility
- Results in measurable or observable output
```


## **Title Guidelines**

### **Format Patterns**
- **Bug:** `[Bug] Brief description of the problem`
- **Feature:** `[Feature] Brief description of the functionality`
- **Task:** `[Task] Brief description of the work`
- **Documentation:** `[Docs] Brief description of the documentation need`

### **Best Practices**
- Keep titles under 60 characters
- Use active voice and clear language
- Avoid technical jargon in titles
- Include affected component if relevant (e.g., `[Bug] SignIn: Email validation fails`)

## **CLI Command Generation**

### **Basic Structure**
```bash
gh issue create \
  --repo <github-org-name>/<github-repo-name> \
  --title "Issue Title" \
  --body "$(cat <<'EOF'
Issue body content here
EOF
)" \
  --assignee "username"
```

## **Assignee Guidelines**
- Assign to requester if they're a team member
- Assign to domain expert for complex technical issues
- Leave unassigned for general tasks that can be picked up by any team member

## **Workflow Process**

### **1. Information Extraction**
- Parse user input for issue type, priority, and details
- Identify missing information and ask clarifying questions
- Determine appropriate template

### **2. Issue Generation**
- Select appropriate template based on issue type
- Fill in provided information
- Generate meaningful title following format guidelines
- Select relevant assignees

### **3. User Review**
Present the generated issue (title, body, assignees) and GitHub CLI command for user approval before proceeding.

### **4. Command Execution**
- Present the complete GitHub CLI command
- Explain any additional steps needed
- Provide follow-up actions (linking to related issues, notifying team members)

## **Quality Guidelines**

### **Issue Body Requirements**
- Use clear, actionable language
- Include specific acceptance criteria (no checkboxes)
- Focus on user needs and business value
- Provide sufficient context for implementation
- Link related issues and dependencies

### **Avoid Anti-patterns**
- ❌ Vague titles like "Fix login"
- ❌ Using checkbox lists in acceptance criteria
- ❌ Implementation details in acceptance criteria
- ❌ Duplicate issues without cross-referencing
- ❌ Missing reproduction steps for bugs
- ❌ Feature requests without user stories

### **Enhancement Opportunities**
- Reference existing code files when relevant
- Include links to design mockups or specifications
- Mention potential implementation approaches (but don't prescribe)
- Consider breaking large features into smaller issues
- Add time estimates or complexity indicators when helpful

## **Post-Creation Actions**

### **Required Issue Link**
**REQUIRED:** Always end your message with a hyperlink to the created issue in markdown format:
```markdown
🔗 [**Issue #[number]:**](https://github.com/<github-org-name>/<github-repo-name>/issues/[number])
```

This link should be the very last line of your response to ensure users can easily access the issue.

## **Integration Notes**

- Cross-reference with existing issues using GitHub's linking syntax
- Use GitHub's auto-closing keywords when creating related PRs
- Consider creating issue templates in the repository for consistency
- Monitor issue metrics and adjust templates based on team feedback
