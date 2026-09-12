# mcp-snippetbox

Learning MCP: tiny notes server with five tools

## Install

```bash
pip install -r requirements.txt
```

## Usage

```bash
# claude_desktop_config.json  (use ABSOLUTE paths: Claude does not
# run from the repo directory, so a bare "server.py" is not found)
# {
#   "mcpServers": {
#     "notes-box": {
#       "command": "python",
#       "args": ["/abs/path/to/mcp-snippetbox/server.py"],
#       "env": {"MCP_NOTES_FILE": "/abs/path/to/notes.json"}
#     }
#   }
# }
python server.py --help
```

## What it does

- Five tools: add / get / update / delete / list notes
- Atomic saves (temp file + os.replace) behind a write lock
- Notes path set by MCP_NOTES_FILE or --notes-file
- Includes a Claude Desktop config snippet with absolute paths
- Every tool carries a real docstring, so clients get descriptions
- A missing note raises instead of returning the string 'not found'

## Project structure

```text
├── .github/
│   └── workflows/
│       └── ci.yml
├── docs/
│   ├── roadmap.md
│   └── usage.md
├── tests/
│   └── test_notes.py
├── .gitignore
├── CHANGELOG.md
├── CODE_OF_CONDUCT.md
├── CONTRIBUTING.md
├── LICENSE
├── SECURITY.md
├── requirements.txt
└── server.py
```

## Development

```bash
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
python -m pytest -q
```

## License

MIT - see [LICENSE](LICENSE).
