# Ruff

[Usage of Ruff Linting and Formatting Example](https://github.com/astral-sh/ruff?tab=readme-ov-file#usage)

[[_TOC_]]

---

# Linting

Check the code for errors:

```bash
ruff check <path/file>
```

Check and fix the code:

```bash
ruff check --fix <path/file>
```

Check and fix the code with ignore list:

```bash
ruff check --fix --ignore <RULES> <path/file>
```

- Example: `F403` : `ami_ec.py:3:1: F403 `from scripts.ui import *` used; unable to detect undefined names`

    Ignore this fixing message by `--ignore F` or `--ignore F403`

    ```bash
    ruff check --ignore F --fix <path/file>
    ```

---

# Formatting

Format the code:

```bash
ruff format <path/file>
```
