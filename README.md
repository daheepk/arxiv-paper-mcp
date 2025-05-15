# 🧠 arXiv Research Assistant MCP Server

[![smithery badge](https://smithery.ai/badge/arxiv-paper-mcp)](https://smithery.ai/server/arxiv-paper-mcp)


This project is an MCP (Model Context Protocol) server built to interact with the vast arXiv.org paper database.

It allows clients like **Claude AI** to search, explore, and compare arXiv papers efficiently — all through a custom-built, local server. It’s built with **Python** and the **FastMCP** framework, and uses **uv** for lightweight package management.

<table>
  <tr>
    <td>
      <a href="https://glama.ai/mcp/servers/@daheepk/arxiv-mcp-server">
        <img width="380" height="200" src="https://glama.ai/mcp/servers/@daheepk/arxiv-mcp-server/badge" alt="arXiv Research Assistant Server MCP server" />
      </a>
    </td>
    <td style="vertical-align: top; padding-left: 10px;">
      <a href="https://mseep.ai/app/daheepk-arxiv-paper-mcp">
        <img src="https://mseep.net/pr/daheepk-arxiv-paper-mcp-badge.png" alt="MseeP.ai Security Assessment Badge" width="140" />
      </a>
    </td>
  </tr>
</table>


## ✨ Features

- **🔍 Keyword-based Paper Search**  
  Search arXiv papers by keywords, with options to sort by relevance or most recent.

- **📚 Latest Papers by Category**  
  Specify an arXiv category code (e.g., `cs.AI`, `math.AP`) to fetch the most recent papers in that field.

- **📄 Paper Details Lookup**  
  Fetch detailed metadata using a paper's arXiv ID: title, authors, abstract, categories, DOI, PDF link, and more.

- **🧑‍🔬 Author-based Paper Search**  
  Retrieve a list of papers published by a specific author.

- **📊 Trend Analysis (Experimental)**  
  Get an overview of trending keywords or topics based on recent papers in a category (currently uses mock data).

- **📝 Summarization Prompt Generator**  
  Dynamically generate prompts that help LLMs summarize a selected paper more effectively.

- **🆚 Comparison Prompt Generator**  
  Provide two paper IDs to generate a structured prompt for comparing their content.

---

## 🛠️ Tech Stack

- Python 3.11+
- [FastMCP](https://github.com/modelcontextprotocol/fastmcp)
- uv (for dependency & environment management)
- requests (for API communication)
- xml.etree.ElementTree (for parsing XML responses)

---

## 🚀 Getting Started

### Installing via Smithery

To install arXiv Research Assistant MCP Server for Claude Desktop automatically via [Smithery](https://smithery.ai/server/arxiv-paper-mcp):

```bash
npx -y @smithery/cli install arxiv-paper-mcp --client claude
```

### Installation from PyPI

```bash
uv pip install arxiv-paper-mcp
```

### 🔧 Clone the repository (for development)
```bash
git clone https://github.com/daheepk/arxiv-mcp-server.git
cd arxiv-mcp-server
```
### 🔧 Install Dependencies (for development)

Use `uv` to install all dependencies in editable mode:

```bash
uv pip install -e .
```


## ⚙️ How to Run

### ▶️ Run the server (locally)

```bash
arxiv-paper-mcp
```

## 🔌 Use with Claude

To use this MCP server with Claude, add the following JSON configuration to Claude's MCP settings:

```json
{
  "mcpServers": {
    "arXivPaper": {
      "command": "uv",
      "args": [
        "tool",
        "run",
        "arxiv-paper-mcp"
      ]
    }
  }
}
```

## Project Structure
```
arxiv-mcp-server/
├── arxiv_mcp/              # Main package
│   ├── __init__.py
│   ├── app.py              # FastMCP app setup
│   ├── server.py           # Server entry point
│   ├── utils.py            # arXiv API communication logic
│   ├── resources/          # MCP resources (categories, authors, etc.)
│   ├── tools/              # MCP tools (search, detail lookup, trends)
│   └── prompts/            # Prompt templates (summarize, compare)
├── pyproject.toml          # Project config & dependencies
└── README.md               # This file
```
