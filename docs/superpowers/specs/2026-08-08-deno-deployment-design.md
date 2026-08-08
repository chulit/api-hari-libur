# Deno Deployment Design Specification - API Hari Libur

**Date:** 2026-08-08  
**Project:** API Hari Libur (`api-hari-libur`)  
**Target Platform:** Deno Deploy (Serverless Deno Runtime)

---

## 1. Overview & Architecture

API Hari Libur is a Deno-based HTTP REST API built using the [Hono](https://hono.dev) framework, serving Indonesian public holiday data and static files, backed by Deno KV for data caching/storage.

### Key Technical Specs:
- **Runtime:** Deno
- **Framework:** Hono (`@hono/hono`)
- **Entry point:** `src/main.ts`
- **Static files:** `public/` directory (served via Hono `serveStatic`)
- **State / Database:** `Deno.openKv()` (Native Deno KV)
- **Configuration:** `deno.json`

---

## 2. Deployment Methods

### Method A: Direct Dashboard Deployment (Deno Deploy UI)
1. User logs in to [dash.deno.com](https://dash.deno.com).
2. Click **New Project** -> **Deploy from GitHub repository**.
3. Select repository `api-hari-libur` and branch `main`.
4. Set entry point to `src/main.ts`.
5. Deploy. Deno Deploy automatically manages builds, SSL certificates, Deno KV database instance, and preview deployments for Pull Requests.

### Method B: Automated GitHub Actions Workflow
Create `.github/workflows/deploy.yml` to run linting and format checks, followed by deploying to Deno Deploy using `deployctl`.

#### Workflow Specification:
- **Trigger:** Push to `main` branch or manual trigger (`workflow_dispatch`).
- **Steps:**
  1. Checkout code.
  2. Setup Deno runtime environment.
  3. Run `deno fmt --check` (optional code quality check).
  4. Run `deno lint` (optional static analysis).
  5. Run `denoland/deployctl` action with:
     - `project`: Deno Deploy project name
     - `entrypoint`: `src/main.ts`

---

## 3. Self-Review & Verification

- **Placeholder scan:** None.
- **Internal consistency:** Entrypoint matches `src/main.ts` and `deno.json` task configuration.
- **Scope check:** Focused purely on deployment configuration and GitHub workflow setup.
- **Ambiguity check:** Clear paths for both zero-config UI deployment and CI/CD workflow.
