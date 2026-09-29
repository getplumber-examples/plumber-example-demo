# Plumber demo project

[![Plumber Score](https://score.getplumber.io/github.com/getplumber-examples/plumber-example-demo.svg)](https://score.getplumber.io/github.com/getplumber-examples/plumber-example-demo)

A GitHub Actions workflow with five CI/CD risks that anyone can understand, for demoing [Plumber](https://github.com/getplumber/plumber).

Scan it:

```bash
plumber analyze --provider github --github-url github.com --project getplumber-examples/plumber-example-demo
```

| Finding | What it means |
|---|---|
| ISSUE-703 | The workflow uses `tj-actions/changed-files` v44, a version with a published security advisory (the March 2025 compromise). |
| ISSUE-411 | A step downloads a script from the internet and runs it unchecked (`curl \| bash`). |
| ISSUE-501 | The `main` branch is not protected: anyone with write access can push to it without review. |
| ISSUE-207 | The pull request title is pasted into a shell command, so a crafted title runs as code. |
| ISSUE-102, ISSUE-103 | The job image `node:latest` can change at any time and is not pinned by digest. |

`.plumber.yaml` trusts the `tj-actions` org, to show that a trusted source is not the same as a safe version: the advisory is still reported.

The workflow only runs on pull requests and never needs to: this repository exists to be scanned. Fix a finding, re-run the scan, and watch the score change.
