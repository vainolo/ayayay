---
applyTo: "**/*.ps1"
---

# PowerShell Script Patterns

## Script Safety Defaults

- Prefer strict, fail-fast script defaults unless a script has a specific reason not to: `Set-StrictMode -Version Latest` and `$ErrorActionPreference = "Stop"`.

## Terminal & Process Management

When spawning new terminal windows on Windows:
- Use `Start-Process pwsh -ArgumentList "-NoExit", "-Command", $command` to launch commands in new terminal
- The `-NoExit` flag keeps window open after command completes (useful for interactive sessions)
- Quote paths properly: `"$variable"` to handle spaces
- For background processes without terminal, use `Start-Job` or `Start-Process -WindowStyle Hidden`

## Function Parameter Design

- Make parameters optional with meaningful defaults: `[Parameter(Mandatory = $false)] [string]$Param = "default"`
- Use `[string]::IsNullOrWhiteSpace()` to check for empty strings/null values (more permissive than `-not`)
- When providing defaults, carefully consider whether the Default parameter itself should be optional
- For helper functions that may be called with or without defaults, mark `Default` parameter as optional: `[Parameter(Mandatory = $false)] [string]$Default = ""`

## Configuration Consolidation

- Create shared config loading functions that handle validation and path resolution
- Use `Get-WorkspaceRoot()` patterns to support scripts in subdirectories (e.g., test/ folder)
- Validate required config keys in the loader, not in each consuming script
- Use helper functions like `Get-ConfigString()`, `Get-ConfigInt()` to reduce repeated config access patterns
- Return structured objects with Config, ConfigPath, and RootDir properties for consistency

## Authentication & Context

- Conditionally pass auth parameters to `Connect-AzAccount` based on config presence: `$connectParams = @{}; if ($config.tenantId) { $connectParams["TenantId"] = $config.tenantId }`
- Use splatting (`@connectParams`) to pass variable sets of parameters
- Check for existing context before forcing re-authentication: `Get-AzContext -ErrorAction SilentlyContinue`

## Long-Running Operations & Monitoring

When handling long-running processes (infrastructure deployments, provisioning, downloads):

- **Prefer log files over terminal output buffering**: For operations taking >30 seconds, read log files directly instead of relying on terminal output. Terminal buffering can mask progress and delay identification of issues.
  
- **Read logs from disk for status verification**: Instead of examining terminal output history, use `Get-Item logfile | Select-Object Length, LastWriteTime` to check if operations completed, or `Get-Content logfile -Tail N` to see recent entries.

- **Pre-examine deployment scripts before execution**: Before running infrastructure deployment scripts, inspect the script to understand required configuration keys, resource dependencies, and expected outcomes. This prevents discovering missing config after lengthy operations fail.

- **Use temporary polling with file-based validation**: When monitoring async operations, periodically read log files instead of continuous terminal output monitoring. Check both file size changes and timestamp updates to determine if operation is still executing.

- **Document operation timeline expectations**: For predictable phases (VM creation ~1-2 min, software provisioning ~5-10 min), set realistic timeouts and avoid polling too frequently.

## Log File Conventions

Scripts that produce logs should:
- Write logs to the path derived from configuration (e.g., `Initialize-Log` with `logPath` config)
- Use consistent timestamp format (e.g., `[yyyy-MM-dd HH:mm:ss]`)
- Provide completion markers (e.g., `=== Provisioning Complete ===`) for easy log validation
- Ensure log writes are not buffered excessively; flush periodically for real-time visibility
