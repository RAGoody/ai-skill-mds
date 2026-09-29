---
name: python-powershell-scaffolder
description: Generates a copy-pasteable, single-line Windows PowerShell command to scaffold a Python project, subdirectories, virtualenv, .gitignore, and requirements.txt without interactive paste errors.
---

# Python PowerShell Scaffolder (Single-Line CLI)

Generates a copy-pasteable single-line PowerShell command string to initialize a complete Python project layout directly in Windows PowerShell or Windows Terminal without interactive line continuation hangs (`>>`).

## When to Use

- Setting up or initializing a new Python project on Windows via PowerShell.
- Generating `.gitignore`, `requirements.txt`, directory layout, and virtual environment setup runnable as an immediate one-liner.
- Avoiding interactive terminal paste bugs, line-break drops, or unclosed quote/brace hangs (`>>`).

## Input Variables

Prompt or inspect for:

- **`project_name`**: Root directory name (e.g., `my_app`).
- **`package_names`**: Comma-separated or list of target dependencies (e.g., `numpy, pytest, readchar, pandas`).
- **`subdirectories`**: Folder paths to create (e.g., `utility, data\input, data\output, config`).
- **`venv`** *(optional, default: true)*: Whether to create and activate `.venv`.

## Generation Template (PowerShell One-Liner)

The output must be formatted strictly as a single continuous line using semicolons `;` between statements and string arrays `@(...) | Set-Content` instead of multi-line here-strings (`@"..."@`):

```powershell
New-Item -ItemType Directory -Force -Path '<project_name>' | Out-Null; Set-Location '<project_name>'; @(<subdirectories_quoted_comma_separated>) | ForEach-Object { New-Item -ItemType Directory -Force -Path $_ | Out-Null }; @(<package_dirs_quoted_comma_separated>) | ForEach-Object { New-Item -ItemType File -Force -Path (Join-Path $_ '__init__.py') | Out-Null }; @('__pycache__/', '*.py[cod]', '*$py.class', '*.so', 'build/', 'dist/', '*.egg-info/', '.env', '.venv/', 'env/', 'venv/', '.pytest_cache/', '.coverage', 'htmlcov/', '.vscode/', '.idea/', '*.swp', '.DS_Store', 'Thumbs.db') | Set-Content -Encoding utf8 '.gitignore'; @(<packages_quoted_comma_separated>) | Set-Content -Encoding utf8 'requirements.txt'; @('def main():', '    print(\"<project_name> initialized!\")', '', 'if __name__ == \"__main__\":', '    main()') | Set-Content -Encoding utf8 'main.py'; @('# <project_name>', '', '## Setup', '```powershell', 'py -m venv .venv', '.\.venv\Scripts\Activate.ps1', 'pip install -r requirements.txt', 'python main.py', '```') | Set-Content -Encoding utf8 'README.md'; py -m venv .venv; & '.\.venv\Scripts\Activate.ps1'; python -m pip install --upgrade pip; pip install -r requirements.txt;