---
name: python-powershell-scaffolder
description: Generates a copy-pasteable, single-line Windows PowerShell command to scaffold a Python project, subdirectories, virtualenv, .gitignore, and requirements.txt without interactive paste errors.
---

## Input Variables

Prompt or inspect for:

- **`project_name`**: Root directory name (e.g., `my_app`).
- **`package_names`**: Comma-separated or list of target dependencies (e.g., `numpy, pytest, readchar, pandas`).
- **`subdirectories`**: Folder paths to create (e.g., `utility, data\input, data\output, config`).
- **`venv`** *(optional, default: true)*: Whether to create and activate `.venv`.

## Structured Prompt Template

```text
As a software engineer, generate a single-line series of powershell commands that creates a Python program scaffolding that can be cut and paste into a Powershell CLI with these specific outcomes:
> creates a directory of the $project_name
> requirements.txt with $packages included where $packages is a comma delimited list.
> .gitignore with appropriate for Python entires
> $project_name.py created with imports for the $packages
> creates $subdirectories where $subdirectories is a comma delimited list.
> executes pip install -r requirements.txt
> includes the code in the appropriate curly braces for execution as a single line of commands.

Variables:
$project_name=testScaffold
$packages=numpy,pandas
$subdirectories=data/input,data/output,utilities

Example output:
& { $p='testScaffold'; $pkg='numpy,pandas'.Split(','); $sub='data/input,data/output,utilities'.Split(','); New-Item -ItemType Directory -Force -Path $p | Out-Null; Set-Location $p; $sub | ForEach-Object { New-Item -ItemType Directory -Force -Path $_ | Out-Null }; @('__pycache__/', '*.py[cod]', '*.so', 'build/', 'dist/', '*.egg-info/', '.env', '.venv/', 'env/', 'venv/', '.vscode/', '.idea/') | Set-Content -Encoding utf8 '.gitignore'; $pkg | Set-Content -Encoding utf8 'requirements.txt'; ($pkg | ForEach-Object { "import $_" }) + @('', 'def main():', "    print('$p initialized successfully')", '', 'if __name__ == "__main__":', '    main()') | Set-Content -Encoding utf8 "$p.py"; pip install -r requirements.txt }