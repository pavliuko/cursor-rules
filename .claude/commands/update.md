Update the `README.md` file with an up-to-date, structured summary of all `.mdc` Cursor rules, `.md` Claude instructions, and `.md` documents in the repository. This command ensures the documentation reflects the current state of the rule set.

## Step-by-Step Instructions

### Step 1: Discover Rules

- Recursively scan the repository for all files with `.mdc` extension.
- Ignore test or example directories unless they are explicitly marked for inclusion.

### Step 2: Extract Metadata

For each `.mdc` file found:
- Parse the file and extract the following:
  - **Rule name** – Typically from a `name` or `title` field in the YAML frontmatter, or a top-level heading.
  - **Description** – A short explanation of the rule's purpose.
  - **Tags or categories** – Optional; may assist with logical grouping.
  - **Relative path** – Used to generate Markdown hyperlinks.

If any field is missing:
- Use the filename (without extension) as the rule name.
- Use *No description provided.* as a fallback.

### Step 3: Organize Rules

- Group rules by **logical categories**, inferred from:
  - Tags (e.g., `style`, `performance`, `config`)
  - Common keywords in file names or descriptions (e.g., "TODO", "length", "import")
- Automatically determine and label each group.
- Group titles must be:
  - Human-readable
  - Descriptive
  - Prefixed with an appropriate **emoji** (e.g., 🧹 Clean Code, 🛠️ Configuration)
- Sort rules **alphabetically by rule name** within each group.
- Place any uncategorized rules into a default `🌀 Miscellaneous` section.

### Step 4: Claude

- Repeat steps 1-3 for all `.md` files in the `claude` folder and subfolders.

### Step 5: Documentation

- Repeat steps 1-3 for all `.md` files in the `docs` folder.

### Step 6: Generate README Content

Dynamically build the `README.md` file using the structure below:

```markdown
# Purpose

<Generated description about the contents and intent of this rule set>

## Cursor

<This entire section must be generated>

- Each group should start with a third-level heading (###) using an emoji and a human-readable name.
- Each rule should appear as a Markdown bullet with a link to the file and a short description.
- All hyperlinks must be relative to the root of the repository.

## Claude

<This entire section must be generated>

- Each group should start with a third-level heading (###) using an emoji and a human-readable name.
- Each rule should appear as a Markdown bullet with a link to the file and a short description.
- All hyperlinks must be relative to the root of the repository.

## Documentation

<This entire section must be generated>

- Each group should start with a third-level heading (###) using an emoji and a human-readable name.
- Each rule should appear as a Markdown bullet with a link to the file and a short description.
- All hyperlinks must be relative to the root of the repository.

## License

<This entire section must be generated>

- Detect whether a `LICENSE` or `LICENSE.md` file exists at the root of the repository.
- If found:
  - Extract the license type from the first few lines (e.g., MIT, Apache 2.0).
  - Add a one-line summary such as:
    - *This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.*
- If no license is present:
  - Add a placeholder line:
    - *No license file found. Please add a LICENSE file to clarify usage rights.*

```

### Step 7: Update README

- Overwrite the existing `README.md` file with the newly generated content.
- Ensure valid Markdown formatting and correct relative paths.
- Skip the update if no changes are detected.

### Notes

- Emojis should be thoughtfully selected and consistently used for visual clarity.
- Escape Markdown-sensitive characters in file names or descriptions as needed.
- Keep section headers concise and under 80 characters.
