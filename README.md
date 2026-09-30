<div align="center">

# ⚡ FreeRoute for Claude Code

**Run Claude Code through OpenRouter with a free model in a few minutes.**

No proxy. No Docker. Just a local config and a tiny launcher.

[![OpenRouter](https://img.shields.io/badge/Powered%20by-OpenRouter-7C3AED?style=for-the-badge)](https://openrouter.ai/)
[![Claude Code](https://img.shields.io/badge/Works%20with-Claude%20Code-D97757?style=for-the-badge)](https://docs.anthropic.com/en/docs/claude-code/overview)
[![Model](https://img.shields.io/badge/Default-Nemotron%203%20Ultra-16A34A?style=for-the-badge)](https://openrouter.ai/nvidia/nemotron-3-ultra-550b-a55b%3Afree)

**[Quick start](#-quick-start) · [How it works](#-how-it-works) · [Troubleshooting](#-troubleshooting)**

</div>

---

> [!IMPORTANT]
> “Free” refers to the selected OpenRouter model, not a Claude Code subscription. Free model availability and rate limits can change. Claude Code is designed for Anthropic models; third-party models may have tool or compatibility issues.

## ✨ What you get

| | |
| --- | --- |
| 🧠 **Free default model** | NVIDIA Nemotron 3 Ultra (`nvidia/nemotron-3-ultra-550b-a55b:free`) |
| 🔀 **Direct routing** | Claude Code → OpenRouter → selected model |
| 🔐 **Local credentials** | Your key stays in `.claude/settings.local.json`, which Git ignores |
| 🎛️ **Easy switching** | Change model IDs in one config file |

## 🚀 Quick start

**Prerequisites:** macOS, Linux, or WSL; Python 3; [Claude Code](https://docs.anthropic.com/en/docs/claude-code/overview) installed and available as `claude`; and an [OpenRouter API key](https://openrouter.ai/keys).

```bash
git clone https://github.com/kvianAR/claude-code-freeroute.git
cd claude-code-freeroute
cp .claude/settings.example.json .claude/settings.local.json
chmod 600 .claude/settings.local.json
```

Open `.claude/settings.local.json` in your editor and replace `PASTE_YOUR_OPENROUTER_KEY_HERE` with your own OpenRouter key. Keep the key inside the quotes. Then start Claude Code:

```bash
./start-claude
```

Inside Claude Code, run `/status`. It should show `ANTHROPIC_AUTH_TOKEN` as the auth source and `https://openrouter.ai/api` as the base URL. You can also check your [OpenRouter activity](https://openrouter.ai/activity) after sending a prompt.

> [!TIP]
> On Windows, use WSL for the commands above. The launcher uses Python 3 and runs inside your terminal.

## 🔍 How it works

```text
Your prompt
    ↓
start-claude  →  reads your local settings
    ↓
Claude Code   →  OpenRouter's Anthropic-compatible endpoint
    ↓
NVIDIA Nemotron 3 Ultra (free)
```

`start-claude` loads the `env` values from `.claude/settings.local.json` **before** launching Claude Code. This helps the first-run sign-in flow use your OpenRouter token. The script does not print or upload your key; Claude Code sends requests to the configured OpenRouter endpoint.

The config sets the main model plus the Opus, Sonnet, Haiku, and subagent roles to the same OpenRouter model. To try another model, replace those model IDs with the exact slug from the [OpenRouter model catalog](https://openrouter.ai/models), then restart Claude Code. Choose a model with tool-use support for coding tasks.

## 🛠️ Troubleshooting

| What you see | What to check |
| --- | --- |
| Anthropic sign-in screen or “credit balance too low” | Start with `./start-claude`, then check `/status`. If you previously signed in with Anthropic, run `/logout` once and relaunch. |
| “Model not found” | Confirm the model slug on OpenRouter, and check for a cached Anthropic login or another API key in your shell. |
| Authentication error | Check your OpenRouter key and ensure `ANTHROPIC_API_KEY` is exactly `""` in the config. |
| Tool calls or complex tasks fail | Try another model. OpenRouter only guarantees Claude Code compatibility with Anthropic's first-party provider. |
| Free model is unavailable or rate limited | Check the model page and OpenRouter limits; retry later or select a different model. |

## 🔒 Keep your key private

`.claude/settings.local.json` is ignored by Git. Only `.claude/settings.example.json` belongs in a public repository. Never paste a real key into an issue, screenshot, commit, or README. If one was exposed, **revoke it in [OpenRouter Keys](https://openrouter.ai/keys) and create a new one**.

## 📚 References

- [OpenRouter's Claude Code integration guide](https://openrouter.ai/docs/guides/coding-agents/claude-code-integration)
- [NVIDIA Nemotron 3 Ultra free model](https://openrouter.ai/nvidia/nemotron-3-ultra-550b-a55b%3Afree)
- [Claude Code documentation](https://docs.anthropic.com/en/docs/claude-code/overview)

---

<div align="center"><sub>Community setup guide. Not affiliated with Anthropic, OpenRouter, or NVIDIA.</sub></div>
