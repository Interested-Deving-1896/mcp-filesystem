[update-readmes]   Mode: rewrite — migrating to template structure...
# mcp-filesystem

[![Built with Ona](https://ona.com/build-with-ona.svg)](https://app.ona.com/#https://github.com/Interested-Deving-1896/mcp-filesystem)

<!-- AI:start:what-it-does -->
_Description pending._
<!-- AI:end:what-it-does -->

## Architecture

<!-- AI:start:architecture -->
_Architecture documentation pending._
<!-- AI:end:architecture -->

## Install

<!-- Add installation instructions here. This section is yours — the AI will not modify it. -->

```bash
git clone https://github.com/Interested-Deving-1896/mcp-filesystem.git
cd mcp-filesystem
```

## Usage


### Option A: Docker (recommended for remote/SMB access)

1. Clone and configure:

```bash
git clone https://github.com/max-rousseau/mcp-yamlfilesystem.git
cd mcp-yamlfilesystem
cp .env.example .env
cp config/config.example config/config
chmod 600 config/config
```

2. Edit `config/config` with your YAML source (see [Configuration](#configuration) below). The config file mount is **required** — the container will not start without it.

3. For local mode, add a data volume to `docker-compose.yml`:

```yaml
volumes:
  - ./config/config:/home/mcp/.config/mcp-yamlfilesystem/config:ro
  - /path/to/your/yaml/files:/data:rw
```

4. Build and start:

```bash
docker compose up -d --build
```

5. Add to Claude Desktop (`~/Library/Application Support/Claude/claude_desktop_config.json`):

```json
{
  "mcpServers": {
    "yaml-filesystem": {
      "command": "npx",
      "args": ["mcp-remote", "http://127.0.0.1:8000/mcp"]
    }
  }
}
```

### Option B: pipx (recommended for local directories)

1. Install:

```bash
pipx install mcp-yamlfilesystem
```

2. Add to Claude Desktop (`~/Library/Application Support/Claude/claude_desktop_config.json`):

```json
{
  "mcpServers": {
    "yaml-filesystem": {
      "command": "mcp-yamlfilesystem",
      "args": ["--local-path", "/path/to/your/yaml/files"]
    }
  }
}
```

For SMB access via pipx, copy `config/config.example` to `~/.config/mcp-yamlfilesystem/config` and configure the SMB settings there.

### Configuration

Edit `config/config` (Docker) or `~/.config/mcp-yamlfilesystem/config` (pipx). See `config/config.example` for all options.

**Local directory:**
```
MCP_FILESYSTEM_LOCAL_PATH=/data
```

**SMB network share:**
```
MCP_FILESYSTEM_SMB_PATH=//nas.local/homeassistant/config
MCP_FILESYSTEM_SMB_USER=your_username
MCP_FILESYSTEM_SMB_PASSWORD=your_password
MCP_FILESYSTEM_SMB_IGNORE_DIRS=deps,.storage,backups,__pycache__
```

### Available Tools

| Tool | Description |
|------|-------------|
| `read_file` | Read contents of a YAML file |
| `create_file` | Create a new YAML file with syntax validation |
| `update_file` | Surgical edits using SEARCH/REPLACE diff blocks |
| `grep_files` | Search for patterns across YAML files |
| `list_directory_structure` | View directory tree |

### CLI Options

| Flag | Description |
|------|-------------|
| `--local-path PATH` | Path to directory containing YAML files |
| `--test` | Test connection to configured filesystem and exit |
| `--http` | Enable HTTP streaming transport (default: stdio) |
| `--host HOST` | Host address for HTTP transport |
| `--port PORT` | Port for HTTP transport |
| `--path PATH` | Endpoint path for HTTP transport |
| `--oauth-enabled true/false` | Enable/disable OAuth for HTTP mode |
| `--oauth-base-url URL` | Public URL for OAuth callbacks |

## Configuration

<!-- Document configuration options here. This section is yours — the AI will not modify it. -->

## CI

<!-- AI:start:ci -->
_CI documentation pending._
<!-- AI:end:ci -->

## Mirror chain

<!-- AI:start:mirror-chain -->
This repo is maintained in [`Interested-Deving-1896/mcp-filesystem`](https://github.com/Interested-Deving-1896/mcp-filesystem) and mirrored through:

```
Interested-Deving-1896/mcp-filesystem  ──►  OpenOS-Project-OSP/mcp-filesystem  ──►  OpenOS-Project-Ecosystem-OOC/mcp-filesystem
```

Changes flow downstream automatically via the hourly mirror chain in
[`fork-sync-all`](https://github.com/Interested-Deving-1896/fork-sync-all).
Direct commits to OSP or OOC are detected and opened as PRs back to `Interested-Deving-1896`.
<!-- AI:end:mirror-chain -->

## Contributors

<!-- AI:start:contributors -->
_Contributors pending._
<!-- AI:end:contributors -->

## Origins

<!-- AI:start:origins -->
_Original project — no upstream fork._
<!-- AI:end:origins -->

## Resources

<!-- AI:start:resources -->
_No additional resource files found._
<!-- AI:end:resources -->

## License

<!-- AI:start:license -->
[BSD-3-Clause](https://github.com/Interested-Deving-1896/mcp-filesystem/blob/main/LICENSE) © 2026 [Interested-Deving-1896](https://github.com/Interested-Deving-1896)
<!-- AI:end:license -->
