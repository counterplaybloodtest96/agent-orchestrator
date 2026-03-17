# Daniel

Terminal multi-agent assistant with fallback load balancing.

## Install

```bash
cd /home/shawn/daniel
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## Run

```bash
daniel
```

On first run, Daniel asks for:
- API keys
- model IDs
- fallback chains
- Claude mode (`cli` or `api`)
- Codex mode (`cli` or `api`)
- Gemini mode (`cli` or `api`)

If you use a Claude subscription in Claude Code, choose `cli` mode so Daniel calls `claude -p` directly (no Anthropic API key required for Claude).
If you want to use logged-in Codex CLI instead of OpenAI API billing, choose Codex `cli` mode.
If you want Gemini without API key billing, choose Gemini `cli` mode after installing Gemini CLI.

Then Daniel writes:
- `~/.config/daniel/config.json`
- `/home/shawn/tasks/.env` (synced for orchestrator)

## Commands

- `/help`
- `/setup`
- `/task list`
- `/task <id>`
- `/run`
- `/smoke`
- `/service status`
- `/service down <claude|codex|gemini> <minutes|manual>`
- `/service up <claude|codex|gemini>`
- `/allow-dir list`
- `/allow-dir add <path>`
- `/allow-dir rm <path>`
- `impl: <message>`
- `ui: <message>`
- `/quit`

Responses are printed in tagged blocks with `agent`, `role`, and UTC timestamp.
Daniel also shows a small `thinking` spinner while waiting on a provider call.

By default, `/home/shawn` is approved for agent CLI working directories.
Use `/allow-dir` commands to manage additional approved directories.
