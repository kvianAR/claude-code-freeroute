# OpenRouter setup notes

The [README quick start](../README.md#-quick-start) is enough for most users. These notes help when switching models or diagnosing account limits.

## Model IDs

Copy the exact slug from the [OpenRouter model catalog](https://openrouter.ai/models). A `:free` suffix belongs to OpenRouter's model ID. Do not add that suffix to a direct NVIDIA model name. Update `model` and each `ANTHROPIC_DEFAULT_*_MODEL` role in `.claude/settings.local.json`, then restart Claude Code.

## Daily limits

An OpenRouter `429` response mentioning `free-models-per-day` means the account reached its free request quota. Changing to another free model may not reset an account-wide limit. Wait for the quota to reset or review the current limits and credit options in your OpenRouter account. An NVIDIA NIM key is a separate route with separate limits.
