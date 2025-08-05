# Code Formatting

**Always use SwiftFormat for consistent code formatting**

- Run SwiftFormat automatically ONLY after any changes to `*.swift` files
- Use the project's SwiftFormat configuration file
- Ensure consistent code style across the entire codebase

### **Commands**

```bash
# Format all Swift files in the project
swiftformat .

# Format specific files
swiftformat Sources/
```

### **Integration Requirements**

- **Automatic formatting:** SwiftFormat runs automatically on Swift file changes
- **Pre-commit formatting:** All Swift code must be formatted before committing
- **Configuration file:** Use the project's `.swiftformat` configuration
- **No manual formatting:** Rely on SwiftFormat instead of manual code styling

### **Best Practices**

- ✅ Let SwiftFormat handle all code formatting automatically
- ✅ Trust the project configuration for consistent results
- ✅ Run formatting before code reviews
- ❌ Don't manually adjust formatting that SwiftFormat handles
- ❌ NEVER verride the SwiftFormat configuration
