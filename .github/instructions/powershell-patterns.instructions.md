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
