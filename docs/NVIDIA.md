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
