# Frequently asked questions

## Why does `./start-claude` work but `claude` asks me to sign in?

`./start-claude` reads `.claude/settings.local.json` and passes its environment to Claude Code. Running bare `claude` bypasses the launcher. You can use the shell shortcut below if you prefer the shorter command.

## Can Claude Code access my Mac?

Claude Code runs locally with the permissions of your macOS user. It can read and change files and run commands when its tools are allowed. Review its permission prompts and run it from a project directory you trust. The selected model receives the prompts and tool results sent through the configured provider.
