# ZenHub Issue Creation Guidelines

## **Purpose**

When a user requests creating a ZenHub issue, extract relevant details, determine the appropriate issue type, and generate a properly formatted issue using ZenHub MCP functions for the <github-repo-name> project.

## **ZenHub Configuration**

- **<project-name> Workspace ID:** <zenhub-workspace-id>
- **GitHub Project:** https://github.com/<github-org-name>/<github-repo-name>

## **Default Repository**

Use <github-repo-name> (GitHub repository) for all issues

## **Pipeline Configuration**

Available ZenHub pipelines in order:

**All issues are created as Ready for Development by default.**

## **Team Members**

Available assignees with their ZenHub and GitHub IDs:

- **Oleksandr Pavliuk** - ZH: `Z2lkOi8vcmFwdG9yL1plbmh1YlVzZXIvMTk4MzI2OQ`, GH: `pavliuko`

If assignee dosn't mentioned specificaly, assign all issues on **Oleksandr Pavliuk**

## **Issue Type Detection**

Automatically determine issue type development level based on user input:

- **Bug** - Problems, errors, crashes, unexpected behavior
- **Feature** - New functionality, enhancements, user stories, architectural decisions, design proposals, technical recommendations  
- **Task** - Development tasks, refactoring, technical debt

## **Label Management**

### **Default Behavior**
- **Do NOT set labels by default** unless explicitly requested by the user
- Keep the `labels` parameter as an empty array `[]` in most cases

### **When to Apply Labels**
- User explicitly requests specific labels (e.g., "add priority:high label")

### **Label Examples**
Common labels when requested:
- Component-based: `ui-component`, `api`, `auth`, `network`
- Priority: `priority:high`, `priority:medium`, `priority:low`
- Type-specific: `bug`, `enhancement`, `documentation`
- Platform: `ios`, `android`, `web`

### **Anti-patterns**
- ❌ Adding labels without user request
- ❌ Over-categorizing with multiple labels
- ❌ Using labels for information already captured in issue type

## **Issue Templates**

### **Bug Report Template**

```markdown
## 🐛 Problem

*Describe what is not working as expected. Be specific and concise.*

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

### **💡 Proposal Template**

```markdown
## 💡 Proposal Overview

*Brief description of the architectural decision, design change, or technical recommendation.*

## 🎯 Problem Statement

*Describe the current challenge, limitation, or opportunity that requires this proposal.*

## 📋 Proposed Solution

*Detailed explanation of the recommended approach, including:*

- High-level architecture or design changes
- Key components or technologies involved
- Implementation approach

## ✅ Benefits

*Expected advantages of implementing this proposal:*

- Performance improvements
- Code maintainability
- Developer experience enhancements
- Technical debt reduction
- Other relevant benefits

## ⚠️ Considerations & Risks

*Potential challenges, risks, or trade-offs:*

- Implementation complexity
- Breaking changes
- Performance implications
- Migration requirements
- Timeline considerations

## 🔗 Related Resources

*Link to relevant documentation, examples, or discussions.*
```

### **📚 Documentation Template**

```markdown
## 📚 Documentation Need

*Describe the missing or outdated documentation.*

## 🎯 Audience

*Define who the documentation is intended for (e.g., developers, users, contributors).*

## 📝 Content Requirements

*List specific topics, examples, or explanations to include.*

## 📍 Location

*Specify where this documentation should live (README, Wiki, inline comments, etc.).*

## 🔗 Related Documentation

*Reference any related documents, tools, or code.*
```

## **MCP Function Usage**

### **Creating Issues**

Use the appropriate creation function based on repository type, then immediately move to "Ready for development" pipeline:

#### **GitHub Issues** (For <github-repo-name> - Primary Repository)
```
// 1. Create the issue
mcp_zenhub_createGitHubIssue({
  title: "Issue Title", 
  body: "Issue body content",
  repositoryId: "",
  issueTypeId: "appropriate_issue_type_id",
  assignees: ["github_usernames"],
  labels: [] // Empty by default unless user requests specific labels
})

// 2. Move to Ready for development pipeline
mcp_zenhub_moveIssueToPipeline({
  issueId: "created_issue_id",
  pipelineId: "Z2lkOi8vcmFwdG9yL1BpcGVsaW5lLzM0NzEzMjU" // Ready for development
})
```

#### **ZenHub Issues** (For internal ZenHub tracking)
```
// 1. Create the issue
mcp_zenhub_createZenhubIssue({
  title: "Issue Title",
  body: "Issue body content",
  repositoryId: "",
  issueTypeId: "appropriate_issue_type_id",
  assigneeIds: ["assignee_zenhub_ids"],
  labels: [] // Empty by default unless user requests specific labels
})

// 2. Move to Ready for development pipeline
mcp_zenhub_moveIssueToPipeline({
  issueId: "created_issue_id",
  pipelineId: "Z2lkOi8vcmFwdG9yL1BpcGVsaW5lLzM0NzEzMjU" // Ready for development
})
```

## **Title Guidelines**

`(DEV) Component: Brief description`

### **Best Practices**
- Keep titles under 60 characters
- Use active voice and clear language
- Include a prefix to indicate the responsible team: (DEV) for Development.
- Include component/area when relevant
- Examples:
  - `(DEV) SignIn: Email validation fails for special characters`
  - `(DEV): Add biometric authentication to login flow`
  - `(DEV): Refactor NetworkAPI error handling`
  - `(DEV): User onboarding experience`

## **Quality Guidelines**

### **Issue Body Requirements**
- Use clear, actionable language
- Include specific acceptance criteria for features/tasks (no checkboxes)
- Provide reproduction steps for bugs
- Focus on user needs and business value
- Include relevant technical context

### **Avoid Anti-patterns**
- ❌ Vague titles like "Fix login"
- ❌ Missing acceptance criteria
- ❌ Using checkbox lists in acceptance criteria
- ❌ Implementation details in user stories
- ❌ Duplicate issues without cross-referencing
- ❌ Missing reproduction steps for bugs

## **Post-Creation Actions**

### **Required Issue Link**
**REQUIRED:** Always end your message with a hyperlink to the created issue in markdown format:
```markdown
🔗 [**Issue #[number]:**](https://app.zenhub.com/<workspace-id>/[number])
```

This link should be the very last line of your response to ensure users can easily access the issue in ZenHub.