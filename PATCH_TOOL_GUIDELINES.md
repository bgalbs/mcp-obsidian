# Patch Tool Usage Guidelines

## Known Issue: Bullet Points Appearing After Patched Sections

When using the `patch_content` tool to update sections in markdown files, the following section's header may incorrectly have a bullet point prepended to it.

### Example of the Issue
Before patch:
```markdown
## Section 1
Content here

## Section 2
Content here
```

After patching Section 1, Section 2 might become:
```markdown
## Section 1
Updated content

- ## Section 2
Content here
```

## Solutions

### 1. Double Newline Fix (Implemented)
The patch tool now automatically adds double newlines at the end of content to ensure proper paragraph separation. This should prevent most cases of the issue.

### 2. Manual Workarounds for MCP Agents
When instructing MCP agents to use the patch tool, include these guidelines:

```
When using the patch tool:
1. Always ensure your content ends with at least one blank line
2. If replacing a section, include a blank line at the end
3. For section headers, ensure there's a blank line before and after
```

### 3. Content Formatting Best Practices
- Always separate sections with blank lines
- Ensure headers have blank lines before and after them
- When patching content between headers, maintain the blank line separation

## Technical Details
The issue appears to be related to how the Obsidian API interprets markdown context when content is patched. Without proper paragraph breaks (double newlines), the parser may continue list formatting from previous content into subsequent sections.

## Testing Recommendations
After patching a section:
1. Verify the next section's header is intact
2. Check for any unintended list markers (-, *, +)
3. Ensure proper spacing between sections