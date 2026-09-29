---
name: python-cli-scaffolder-bash
description: Generates a copy-pasteable bash script to scaffold a Python project directory, subdirectories, virtualenv, .gitignore, and requirements.txt based on customizable parameters.
---

# Python CLI Scaffolder

Generates a single copy-pasteable bash command sequence to initialize a complete Python project layout directly in your shell.

## When to Use

- Setting up or initializing a new Python project via CLI.
- Generating a customized `.gitignore`, `requirements.txt`, directory layout, and virtual environment setup in one step.
- The user provides or wants to plug in custom package lists and subdirectories.

## Input Variables

If not already supplied, prompt or inspect for:

- **`project_name`**: Root directory name (e.g., `my_app`).
- **`packages`**: List or comma-separated packages for `requirements.txt` (e.g., `fastapi, uvicorn, pytest`).
- **`subdirectories`**: Folder paths to create (e.g., `src/api, src/core, tests`).
- **`venv`** *(optional, default: true)*: Whether to create and activate `.venv`.

## Workflow & Template

Generate a self-contained shell script using heredocs (`cat << 'EOF'`) and `mkdir -p`.

### Bash Generation Blueprint

```bash
mkdir -p <project_name> && cd <project_name>

# Subdirectories
mkdir -p <subdirectories>

# Python package markers
touch <package_subdirs_init_py>

# .gitignore
cat << 'EOF' > .gitignore
__pycache__/
*.py[cod]
*$py.class
*.so
build/
dist/
*.egg-info/
.env
.venv/
env/
venv/
.pytest_cache/
.coverage
htmlcov/
.vscode/
.idea/
*.swp
.DS_Store
EOF

# requirements.txt
cat << 'EOF' > requirements.txt
<package_1>
<package_2>
EOF

# Entrypoint & README
cat << 'EOF' > main.py
def main():
    print("Project initialized!")

if __name__ == "__main__":
    main()
EOF

cat << 'EOF' > README.md
# <project_name>

## Getting Started
\`\`\`bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python main.py
\`\`\`
EOF

# Virtual environment setup
python3 -m venv .venv
source .venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt