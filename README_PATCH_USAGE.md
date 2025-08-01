# Correct Usage of the Patch Tool

## Block References

When using `target_type: "block"`, the `target` parameter should be a block reference ID (e.g., `abc123`), not the actual content.

### Incorrect Usage:
```json
{
  "target_type": "block",
  "target": "- Full content of the block here..."
}
```

### Correct Usage:
```json
{
  "target_type": "block", 
  "target": "abc123"
}
```

Where `abc123` is the block reference ID from a line like `^abc123` in the Obsidian document.

## Heading References

When using `target_type: "heading"`, the `target` should be the heading path using `::` as delimiter:

```json
{
  "target_type": "heading",
  "target": "Main Heading::Subheading::Target Heading"
}
```

## Content Formatting

The Obsidian REST API handles spacing automatically. The MCP server passes content directly to the API without modification to avoid interfering with the API's built-in formatting logic.

If you're experiencing formatting issues:
1. Ensure you're using the correct target type and target format
2. The Obsidian REST API plugin may need to be updated
3. Check if the `Trim-Target-Whitespace` header needs to be set