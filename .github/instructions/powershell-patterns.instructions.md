---
applyTo: "**/*.ps1"
---

# PowerShell Script Patterns

## Terminal & Process Management

When spawning new terminal windows on Windows:
- Use `Start-Process pwsh -ArgumentList "-NoExit", "-Command", $command` to launch commands in new terminal
- The `-NoExit` flag keeps window open after command completes (useful for interactive sessions)
- Quote paths properly: `"$variable"` to handle spaces
- For background processes without terminal, use `Start-Job` or `Start-Process -WindowStyle Hidden`
