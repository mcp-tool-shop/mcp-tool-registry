# MCP Tool Registry

Metadata-only registry for MCP Tool Shop tools.

## Structure

```
mcp-tool-registry/
├── registry.json              # Main tool registry
├── schema/
│   └── registry.schema.json   # JSON Schema for validation
├── bundles/
│   ├── core.json              # Core utilities bundle
│   ├── agents.json            # Agent tools bundle
│   └── ops.json               # Operations bundle
└── .github/
    └── workflows/
        └── validate.yml       # CI validation
```

## Usage

The registry is consumed by the `mcp` CLI tool. Tools are installed via git.

## Adding a Tool

1. Add an entry to `registry.json`
2. Ensure it validates against the schema
3. Submit a PR

## Schema

Each tool requires:
- `id`: kebab-case identifier (e.g., `file-compass`)
- `name`: Human-readable name
- `description`: What the tool does
- `repo`: GitHub repository URL
- `install`: Installation config (`type`, `url`, `default_ref`)
- `tags`: Array of tags for search/filtering
- `defaults` (optional): Default settings like `safe_run`

## Bundles

Bundles are curated collections of tools:
- **core**: Essential utilities
- **agents**: Agent orchestration tools
- **ops**: Operations and infrastructure

## Validation

The registry is validated on every PR/push via GitHub Actions.
