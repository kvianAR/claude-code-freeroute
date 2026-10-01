# OpenRouter setup notes

The [README quick start](../README.md#-quick-start) is enough for most users. These notes help when switching models or diagnosing account limits.

## Model IDs

Copy the exact slug from the [OpenRouter model catalog](https://openrouter.ai/models). A `:free` suffix belongs to OpenRouter's model ID. Do not add that suffix to a direct NVIDIA model name. Update `model` and each `ANTHROPIC_DEFAULT_*_MODEL` role in `.claude/settings.local.json`, then restart Claude Code.
