# ⚡ UV

## 👀 Fast Lookup

- **Package Management** && **Virtual Environment Management** && **SUPER FAST**

## 🧐 What is UV?

UV is an amazing tool for managing Python packages and projects and IT IS SUPER FAST!

## 😎 Cheat Sheet

- **Initialize a new project**
  - `uv init` : Initialize a new project to current directory
  - `uv init <project_name>` : Initialize a new project to `<project_name>` directory

- **Add / Remove dependencies**
  - `uv add <package_name>` : Add a dependency to the project
  - `uv remove <package_name>` : Remove a dependency from the project

- **Run a command / Run a script**
  - `uv run <command>` : Run a command
  - `uv run <script_name>` : Run a script
  - `uv run --python <python_version> <script_name>` : Run a script with a specific Python version

- **List smt**
  - `uv python list` : List available Python versions

- **Sync dependencies**
  - `uv sync` : Sync dependencies from `pyproject.toml` with the virtual environment