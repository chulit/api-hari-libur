# Deno Deployment Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Provide GitHub Actions deployment workflow for Deno Deploy and document Deno Deploy setup for the API Hari Libur project.

**Architecture:** Add `.github/workflows/deploy.yml` utilizing Deno runtime CLI checks (`deno fmt`, `deno lint`) and `denoland/deployctl` action, plus update documentation for zero-config Deno Deploy UI setup.

**Tech Stack:** Deno, GitHub Actions, Deno Deploy (`deployctl`), Markdown.

## Global Constraints

- Entrypoint: `src/main.ts`
- Task config: `deno.json`
- Platform: Deno Deploy

---

### Task 1: Add GitHub Actions Deployment Workflow

**Files:**
- Create: `.github/workflows/deploy.yml`

**Interfaces:**
- Consumes: `src/main.ts`, `deno.json`
- Produces: GitHub Actions deployment configuration for Deno Deploy

- [ ] **Step 1: Create `.github/workflows/deploy.yml`**

```yaml
name: Deploy to Deno Deploy

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Setup Deno
        uses: denoland/setup-deno@v1
        with:
          deno-version: v1.x

      - name: Check code formatting
        run: deno fmt --check

      - name: Lint code
        run: deno lint

      - name: Deploy to Deno Deploy
        if: github.ref == 'refs/heads/main'
        uses: denoland/deployctl@v1
        with:
          project: "api-hari-libur"
          entrypoint: "src/main.ts"
```

- [ ] **Step 2: Verify local formatting and linting**

Run: `deno fmt --check && deno lint`
Expected: Passes formatting and linting checks.

- [ ] **Step 3: Commit workflow file**

```bash
git add .github/workflows/deploy.yml
git commit -m "ci: add Deno Deploy GitHub Actions workflow"
```

---

### Task 2: Update Project Documentation with Deno Deploy Instructions

**Files:**
- Modify: `readme.md`

**Interfaces:**
- Consumes: Deno Deploy project configuration details
- Produces: Updated deployment guide section in `readme.md`

- [ ] **Step 1: Add deployment section to `readme.md`**

Append or update the deployment instructions in `readme.md` to clearly explain both Dashboard and GitHub Actions deployment methods.

- [ ] **Step 2: Commit documentation update**

```bash
git add readme.md
git commit -m "docs: add Deno Deploy deployment instructions"
```
