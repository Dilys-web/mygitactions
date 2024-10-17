# GitHub Actions with Super-Linter

## Overview

This repository demonstrates:
1. The integration of **GitHub Actions** with **Super-Linter** to enforce code quality across various file types (Python, Markdown, YAML).

---

## Section 1: GitHub Actions Workflow with Super-Linter

### What is Super-Linter?

**Super-Linter** is a GitHub-maintained tool that automatically runs multiple linters to ensure your code meets coding standards and best practices across a variety of languages and file types. In this repository, it’s set up to check Python, Markdown, and YAML files.

### Workflow Setup

The **GitHub Actions** workflow is triggered on every push to the repository. It uses **Super-Linter** to check for linting issues across different languages in the codebase.

### 1. **Workflow File: `.github/workflows/superlinter.yml`**

```yaml
name: Super-Linter

on: push

jobs:
  super-lint:
    name: Lint code base
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Run Super-Linter
        uses: github/super-linter@v4
        env:
          DEFAULT_BRANCH: main
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

```

### Explanation:

**on: push:** This workflow runs whenever code is pushed to the repository.

**actions/checkout@v2:** Checks out the repository code so the linter can access it.

**github/super-linter@v4:** Uses the latest version (v4) of Super-Linter to check code quality.

### Environment Variables:
**DEFAULT_BRANCH:** Refers to the main branch of the repository.

**GITHUB_TOKEN:** Automatically provided by GitHub to securely access the repository.

### Supported Linters in this Repository
**Python:** Linted using tools like Black, Flake8, Pylint.

**Markdown:** Checked using Markdownlint.

**YAML:** Checked using Yamllint.
Super-Linter automatically detects the file types and applies the appropriate linters.
