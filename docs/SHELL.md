# Run from your shell

The most reliable command is `./start-claude` from the repository root. A bare `claude` command runs the globally installed client and does not automatically load this repository's local settings.

## Optional zsh shortcut

Add this function to `~/.zshrc`, then open a new terminal:

```zsh
claude() {
  if [[ "$PWD" == "/Users/Apple/Downloads/Claude_Code" ]]; then
    "/Users/Apple/Downloads/Claude_Code/start-claude" "$@"
  else
    command claude "$@"
  fi
}
```

Replace the path with your actual clone location. This affects only shells that read your `~/.zshrc`; VS Code may need a new terminal window.

## Working directory

The launcher changes into its own repository directory before starting Claude Code. Put project files you intend to work on there, or adjust the launcher for a different workflow. Always check Claude Code's displayed working directory before granting file changes.
