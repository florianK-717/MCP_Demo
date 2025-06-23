# Integration des GitHub MCP Servers mit Claude Desktop

## Überblick

In diesem Dokument wird die Integration des GitHub MCP Servers mit Claude Desktop erläutert. MCP (Model Context Protocol) ermöglicht es KI-Tools wie Claude, direkt mit GitHub-Daten zu interagieren, um Aufgaben wie das Erstellen von Repositories, das Verwalten von Pull Requests und das Analysieren von Code durchzuführen.:contentReference[oaicite:4]{index=4}

## Voraussetzungen

- **Claude Desktop** installiert und konfiguriert.
- **Docker** installiert und funktionsfähig.
- **GitHub Personal Access Token (PAT)** mit den notwendigen Berechtigungen erstellt.:contentReference[oaicite:11]{index=11}

## Einrichtung des GitHub MCP Servers

### 1. GitHub Personal Access Token erstellen

Gehe zu [GitHub Personal Access Tokens](https://github.com/settings/tokens) und erstelle ein neues Token mit den folgenden Berechtigungen:​:contentReference[oaicite:14]{index=14}

- `repo`
- `read:org`
- `write:discussion`:contentReference[oaicite:21]{index=21}

Speichere das Token sicher, da es später benötigt wird.:contentReference[oaicite:24]{index=24}

### 2. Konfiguration in Claude Desktop

Füge die folgende Konfiguration in die `settings.json` von Claude Desktop ein:​:contentReference[oaicite:27]{index=27}

```json
{
  "mcpServers": {
    "github": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "-e",
        "GITHUB_PERSONAL_ACCESS_TOKEN",
        "ghcr.io/github/github-mcp-server"
      ],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "<DEIN_TOKEN>"
      }
    }
  }
}
