# GITHUB RULES

## 1. Start a GitHub repository

### 1.1 Create the GitHub repo first

- **License:**
  - MIT if the repo is on a GitHub personal account
  - GNU General Public License v3.0 (GPL-3.0) if the repo is on a GitHub Organization
- Initialize README and description
- **Repo name format:** capitalize the first letter of each word, join words with `_` (e.g. `Agent_Ops`)

### 1.2 Clone the repo to local

- Open PowerShell in `D:\Project`
- Clone:

```powershell
cd D:\Project
git clone https://github.com/<owner>/<Repo_Name>.git
cd <Repo_Name>
code .
```

### 1.3 Change the default branch from `master` to `main`

Do it on GitHub (Settings > Branches > pencil icon next to `master` > rename to `main`), then sync local:

```powershell
git branch -m master main
git fetch origin
git branch -u origin/main main
git remote set-head origin -a
```

Record every step and command actually run.

## 2. GitHub change action

### 2.1 Checkout

- **Never commit on `main`.**
- Check the current branch first:
  - On a working branch: stay on it
  - On `main`: create and switch to a new branch named `tobey/{short-change-name}`

```powershell
git branch --show-current
git checkout -b tobey/<short-change-name>
```

### 2.2 Commit and push

```powershell
git add -A
git commit -m "<area>: <short summary>"
git push -u origin HEAD
```

### 2.3 Create the PR using the GitHub MCP

- Use the GitHub MCP `create_pull_request` tool (base `main`, head = the working branch)
- Use `draft: true` when only asked for a draft
- Title: short area prefix + summary; body: what changed, why, notes for reviewers