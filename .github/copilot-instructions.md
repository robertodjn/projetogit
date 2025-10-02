# Copilot instructions — projetogit

Purpose: short, actionable notes so an AI coding agent can be immediately productive in this tiny repository.

- Repo shape
  - Very small repository. Primary files at the root:
    - `testgit.py` — simple Python script (contains a print and Portuguese comment).
    - `outroteste.py` — another simple script with a short message.
  - No tests, no packaging, no virtual environment files.

- Important quirk (must know)
  - Both Python files currently include Markdown code fences (lines that start with ```). That makes the files invalid Python as-is. Before running or importing these modules, remove any leading/trailing ``` lines.
  - Example quick-run (zsh):
    ```bash
    # run testgit.py after stripping markdown fences
    sed '/^```/d' testgit.py | python3 -
    ```

- How to run / debug
  - There is no build step. Execute scripts directly with the system Python 3 interpreter:
    - `python3 testgit.py` (after removing fences)
  - For quick edits, you can run via the sed pipeline above to avoid editing the file on disk.

- Conventions and patterns (discoverable)
  - Files use UTF-8 and Portuguese comments/strings — keep translations in context when editing messages.
  - The repo currently contains only top-level scripts. New functionality should be added as modules (a new package folder) if it grows.
  - When adding dependencies, add a `requirements.txt` or a `pyproject.toml` so other developers (and agents) can see intent.

- Typical AI tasks that make sense here
  - Remove the markdown fences and convert scripts to well-formed Python modules.
  - Add a short `README.md` that documents the purpose of the repo and how to run the scripts.
  - Add a `requirements.txt` or `pyproject.toml` if external packages are introduced.

- Examples of edits (be conservative)
  - Small fix: remove ``` lines from `testgit.py` and run — verify the output is the printed string.
  - Refactor: create `projetogit/__main__.py` and convert `testgit.py` into `projetogit/cli.py` if you need CLI structure.

- Integration & safety
  - There are no external integrations in this repo. Do not add undocumented network calls or secrets.

- If you update this file
  - Merge intelligently: preserve any human-written guidelines in future versions and keep the "Important quirk" note if the fenced blocks remain.

If anything here is unclear or you'd like more detail (example PR, test harness, or converting scripts to a package), tell me which area to expand.
