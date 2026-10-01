# Frequently asked questions

## Why does `./start-claude` work but `claude` asks me to sign in?

`./start-claude` reads `.claude/settings.local.json` and passes its environment to Claude Code. Running bare `claude` bypasses the launcher. You can use the shell shortcut below if you prefer the shorter command.

## Can Claude Code access my Mac?

Claude Code runs locally with the permissions of your macOS user. It can read and change files and run commands when its tools are allowed. Review its permission prompts and run it from a project directory you trust. The selected model receives the prompts and tool results sent through the configured provider.

## Is a free model the same as free Claude Code usage?

No. The model provider sets its own pricing and limits. OpenRouter free models can have request quotas; NVIDIA NIM uses a separate account and its own quota or credits. Claude Code itself is the local client in this setup.

## Can I switch models later?

Yes. Update the model IDs in your local settings and restart the launcher. Use the exact provider-specific ID; OpenRouter's `:free` suffix is not an NVIDIA NIM suffix.
