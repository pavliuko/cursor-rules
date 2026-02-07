# Pull Request Creation Guidelines

## **Purpose**

When creating pull requests, ensure they are well-structured, informative, and follow the project's conventions to facilitate code review and maintain project history.

## **Pre-Creation Workflow**

### **1. Analyze Changes**
Before creating the PR, analyze the branch changes to understand:
- What files were modified
- The scope and impact of changes
- Any breaking changes or dependencies

### **2. Sync with Remote**
```bash
# Ensure your branch is up to date and pushed
git push -u origin <branch-name>

# Verify GitHub CLI authentication
gh auth status
```

## **PR Title Guidelines**

### **Format**

```
type [#issue]: brief description
```

**Note:** Issue number is optional - omit if no related issue exists.

### **Issue Number Extraction**
Extract issue number from branch name using these common patterns:
- `feat/123-description` → `#123`
- `fix/456-bug-description` → `#456`
- `chore/789-cleanup` → `#789`

### **Title Examples**
- `feat [#456]: add adaptive layout for profile screen`
- `fix [#789]: prevent crash on nil URL in share sheet`
- `chore: update dependencies and clean unused code`
- `refactor: extract authentication logic to package`

### **Best Practices**
- ✅ Keep under 60 characters
- ✅ Use present tense ("add" not "added")
- ✅ Be descriptive but concise
- ✅ Include affected component if relevant
- ❌ Don't include periods at the end
- ❌ Don't use vague terms like "fix stuff" or "improvements"

## **PR Description Template**

Use this structured markdown template:

```markdown
## 📌 Summary
<!-- Briefly describe the purpose of the PR in one or two sentences. -->

## 🛠️ Changes
<!-- Describe WHAT was changed. Use bullet points. Keep it concise and high-level. -->
- 
- 
- 

## ✅ Impact & Risk
<!-- What does this change affect? Consider performance, user experience, reliability, or developer experience. Mention any risks or areas to watch. -->

## 📝 Notes
<!-- Add any relevant context: limitations, tricky logic, follow-ups, or things to double-check. -->

## 🔗 Related Issues
<!-- Link related ZenHub issues or epics. Use full URLs or descriptive references. -->
Closes: [ZenHub Issue URL or Title]  
Refs: [ZenHub Issue URL or Title]
```

## **GitHub CLI Commands**

### **Basic Creation**
```bash
gh pr create \
  --title "feat [#456]: add adaptive layout for profile screen" \
  --body-file pr-description.md \
  --assignee @me
```

### **With Inline Body**
```bash
gh pr create \
  --title "feat [ZenHub #456]: add adaptive layout for profile screen" \
  --body "$(cat <<'EOF'
## 🧾 Summary
Add adaptive layout to enhance UI on larger screens and improve accessibility.

## 🛠️ Changes
- Add responsive layout components
- Implement dynamic type scaling
- Update UI to support landscape mode

## ✅ Impact & Risk
Improved user experience on tablets and better accessibility support.
Minimal risk, but layout regressions should be monitored.

## 📝 Notes
Dark mode optimization will be handled in a follow-up.

## 🔗 Related Issues
Closes: https://app.zenhub.com/workspaces/your-workspace-name/issues/your-org/your-repo/456
EOF
)" \
  --assignee @me
```

### **With Draft Flag**
```bash
gh pr create \
  --draft \
  --title "feat [#456]: add adaptive layout for profile screen" \
  --body-file pr-description.md
```

## **Post-Creation Actions**

### **1. Verification**
```bash
# Verify PR was created successfully
gh pr view
```

### **2. Provide PR Link in Chat**
After successfully creating the PR, always provide the PR link in the chat for easy access:
```bash
# Get the PR URL and display it
gh pr view --web --json url --jq '.url'
```

**REQUIRED:** Always end your message with a hyperlink to the created PR in markdown format:
```markdown
🔗 [**Pull Request:**](https://github.com/owner/repo/pull/123)
```

This link should be the very last line of your response to ensure users can easily access the PR.

## **Troubleshooting**

### **Common Issues**

| Issue                              | Solution                                        |
| ---------------------------------- | ----------------------------------------------- |
| `No commits between base and head` | Ensure you've committed and pushed changes      |
| `GitHub CLI not authenticated`     | Run `gh auth login`                             |
| `Remote branch not found`          | Push branch: `git push -u origin <branch-name>` |
| `PR already exists`                | Use `gh pr view` to see existing PR             |

### **Best Practices for Issues**
- **Missing issue number**: Proceed without issue reference - not all changes require an issue
- **Unclear changes**: Request more detailed description of the changes made