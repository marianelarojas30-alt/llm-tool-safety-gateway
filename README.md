# Claude Ollama Fallback - Valentina

Windows-first continuity helper for Claude Code. It installs a Claude Code `StopFailure` hook and, on supported Claude API failures, prepares a compact handoff and launches Claude Code against a local Ollama model in the same working directory.

## Fast start

1. Install **Claude Code**, **Ollama**, and **Python 3**.
2. Double-click `INSTALL_WINDOWS.bat`.
3. Double-click `PULL_MODEL_WINDOWS.bat`.
4. Double-click `CHECK_WINDOWS.bat`.
5. Work in Claude Code normally.

The default local model is `qwen3.5`. You can change it with the `CLAUDE_OLLAMA_MODEL` environment variable.

## Clone on Windows

```powershell
git clone https://github.com/marianelarojas30-alt/llm-tool-safety-gateway.git
cd llm-tool-safety-gateway
```

Then run `INSTALL_WINDOWS.bat`, `PULL_MODEL_WINDOWS.bat`, and `CHECK_WINDOWS.bat`.

## Files

- `install.py` - installs the continuity hook without deleting existing hooks.
- `continuity.py` - detects supported failures, captures project/session state, and performs the handoff.
- `INSTALL_WINDOWS.bat` - Windows installer.
- `PULL_MODEL_WINDOWS.bat` - downloads the default Ollama model.
- `CHECK_WINDOWS.bat` - runs diagnostics.
- `TEST_TAKEOVER_WINDOWS.bat` - manually tests a takeover.
- `STATUS_WINDOWS.bat` - prints continuity status.
- `FULL_AUTO_ON_WINDOWS.bat` - enables the most autonomous permission mode. Use only in a trusted project.
- `SAFER_MODE_WINDOWS.bat` - returns to the safer permission mode.

## Manual commands

After installation, in PowerShell:

```powershell
& "$env:LOCALAPPDATA\claude-ollama-continuity\bin\claude-continuity.cmd" doctor
& "$env:LOCALAPPDATA\claude-ollama-continuity\bin\claude-continuity.cmd" status
& "$env:LOCALAPPDATA\claude-ollama-continuity\bin\claude-continuity.cmd" manual "continue the unfinished task and verify the result"
```

## Important limitation

Claude Code may compact its context before it reaches an API failure. This repository is a failure/limit handoff mechanism, not a replacement for Claude Code context compaction. The automatic handoff depends on Claude Code emitting a supported `StopFailure` event.
