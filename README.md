# MCP servers

A collection of *reference implementations* for the [Model Context Protocol](https://modelcontextprotocol.io/) (MCP). This repository showcases the versatility and extensibility of MCP, demonstrating how it can be used to give Large Language Models (LLMs) secure, controlled access to tools and data sources.

Each MCP server is implemented with either the [Typescript MCP SDK](https://github.com/modelcontextprotocol/typescript-sdk) or [Python MCP SDK](https://github.com/modelcontextprotocol/python-sdk).

## 🌟 Featured Servers

These servers aim to showcase MCP featuers and the Typescript and Python SDK. They are by no means the full-featured.

- **[Filesystem](src/filesystem)** - Secure file operations with configurable access controls
- **[GitHub](src/github)** - Repository management, file operations, and GitHub API integration
- **[GitLab](src/gitlab)** - GitLab API, enabling project management
- **[Git](src/git)** - Tools to read, search, and manipulate Git repositories
- **[Google Drive](src/gdrive)** - File access and search capabilities for Google Drive
- **[PostgreSQL](src/postgres)** - Read-only database access with schema inspection
- **[Sqlite](src/sqlite)** - Database interaction and business intelligence capabilities
- **[Slack](src/slack)** - Channel management and messaging capabilities
- **[Sentry](src/sentry)** - Retrieving and analyzing issues from Sentry.io
- **[Memory](src/memory)** - Knowledge graph-based persistent memory system
- **[Puppeteer](src/puppeteer)** - Browser automation and web scraping
- **[Brave Search](src/brave-search)** - Web and local search using Brave's Search API
- **[Google Maps](src/google-maps)** - Location services, directions, and place details
- **[Fetch](src/fetch)** - Web content fetching and conversion for efficient LLM usage

## 🌎 Community Servers

There are many community developed and maintained servers.

> **Note:** Community servers are untested and should be used at your own risk. They are not affiliated with or endorsed by Anthropic.

- <img height="12" width="12" src="https://cdn.simpleicons.org/cloudflare" /> **[Cloudflare](https://github.com/cloudflare/mcp-server-cloudflare)** - Deploy, configure & interrogate your resources on the Cloudflare developer platform (e.g. Workers/KV/R2/D1)
- **[Raygun](https://github.com/MindscapeHQ/mcp-server-raygun)** - Interact with your crash reporting and real using monitoring data on your Raygun account
- **[MCP Installer](https://github.com/anaisbetts/mcp-installer)** - This server is a server that installs other MCP servers for you.

## 📚 Resources

- **[Awesome MCP Servers by punkpeye](https://github.com/punkpeye/awesome-mcp-servers)** - A curated list of MCP servers by **[Frank Fiegel](https://github.com/punkpeye)**
- **[Awesome MCP Servers by wong2](https://github.com/wong2/awesome-mcp-servers)** - A curated list of MCP servers by **[wong2](https://github.com/wong2)**
- **[Awesome MCP Servers by appcypher](https://github.com/appcypher/awesome-mcp-servers)** - A curated list of MCP servers by **[Stephen Akinyemi](https://github.com/appcypher)**
- **[mcp-get](https://mcp-get.com)** - Command line tool for installing and managing MCP servers by **[Michael Latman](https://github.com/michaellatman)**

## 🚀 Getting Started

### Using MCP Servers in this Repository
Typescript-based servers in this repository can be used directly with `npx`.

For example, this will start the [Memory](src/memory) server:
```sh
npx -y @modelcontextprotocol/server-memory
```

Python-based servers in this repository can be used directly with [`uvx`](https://docs.astral.sh/uv/concepts/tools/) or [`pip`](https://pypi.org/project/pip/). `uvx` is recommended for ease of use and setup.

For example, this will start the [Git](src/git) server:
```sh
# With uvx
uvx mcp-server-git

# With pip
pip install mcp-server-git
python -m mcp_server_git
```

Follow [these](https://docs.astral.sh/uv/getting-started/installation/) instructions to install `uv` / `uvx` and [these](https://pip.pypa.io/en/stable/installation/) to install `pip`.

### Using an MCP Client
However, running a server on its own isn't very useful, and should instead be configured into an MCP client. For example, here's the Claude Desktop configuration to use the above server:

```json
{
  "mcpServers": {
    "memory": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-memory"]
    }
  }
}
```

Additional examples of using the Claude Desktop as an MCP client might look like:

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/path/to/allowed/files"]
    },
    "git": {
      "command": "uvx",
      "args": ["mcp-server-git", "--repository", "path/to/git/repo"]
    },
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "<YOUR_TOKEN>"
      }
    },
    "postgres": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-postgres", "postgresql://localhost/mydb"]
    }
  }
}
```

## 🛠️ Creating Your Own Server

Interested in creating your own MCP server? Visit the official documentation at [modelcontextprotocol.io](https://modelcontextprotocol.io/introduction) for comprehensive guides, best practices, and technical details on implementing MCP servers.

## 🤝 Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for information about contributing to this repository.

## 🔒 Security

See [SECURITY.md](SECURITY.md) for reporting security vulnerabilities.

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 💬 Community

- [GitHub Discussions](https://github.com/orgs/modelcontextprotocol/discussions)

## ⭐ Support

If you find MCP servers useful, please consider starring the repository and contributing new servers or improvements!

---

Managed by Anthropic, but built together with the community. The Model Context Protocol is open source and we encourage everyone to contribute their own servers and improvements!
