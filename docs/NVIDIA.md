# Direct NVIDIA setup

This route is optional. It uses an NVIDIA NIM key and a local LiteLLM gateway. The OpenRouter quick start does not require it.

## Install the gateway

From the repository root on macOS or Linux:

```bash
python3 -m venv ~/.cache/claude-nvidia-gateway
~/.cache/claude-nvidia-gateway/bin/python -m pip install 'litellm[proxy]'
cp .claude/nvidia-gateway.example.yaml .claude/nvidia-gateway.yaml
```

The launcher currently expects the gateway Python at `~/.cache/claude-nvidia-gateway/bin/python`. Keep `.claude/nvidia-gateway.yaml` local; Git ignores it.

## Configure Claude Code

Create `.claude/settings.local.json` with this shape. Replace the placeholder with your own NVIDIA key; never commit the resulting file.

```json
{
  "model": "nvidia/nemotron-3-ultra-550b-a55b",
  "env": {
    "NVIDIA_NIM_API_KEY": "PASTE_YOUR_NVIDIA_KEY_HERE",
    "ANTHROPIC_API_KEY": "",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "nvidia/nemotron-3-ultra-550b-a55b",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "nvidia/nemotron-3-ultra-550b-a55b",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "nvidia/nemotron-3-ultra-550b-a55b",
    "CLAUDE_CODE_SUBAGENT_MODEL": "nvidia/nemotron-3-ultra-550b-a55b"
  }
}
```

Run `chmod 600 .claude/settings.local.json`, then `./start-claude`. The launcher supplies the local gateway address and an ephemeral gateway token to Claude Code.

## Check the route

In Claude Code, run `/status`. The base URL should be a `127.0.0.1` address while the direct NVIDIA route is active. A normal reply to a short prompt confirms that Claude Code, the local gateway, and NVIDIA are connected. If `/status` still shows Anthropic billing, exit and restart with `./start-claude`.
