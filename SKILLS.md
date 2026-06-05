---
skill: create-github-repo
title: Create GitHub repository
usage: /create-github-repo
description: Reusable task guide for creating a public GitHub repository with README and main branch setup.
---

# Create GitHub repository

This skill documents how to create a new GitHub repository using the GitHub CLI and initialize it for future use.

## Goal
Create a public GitHub repository with:
- `README.md` initialized
- `main` as the default branch
- local clone created at the target path

## Prerequisites
- Install GitHub CLI (`gh`)
- Authenticate with GitHub using `gh auth login`
- Ensure the target GitHub user or organization is correct

## Recommended Command
Use this command from the directory where you want the new repository to be created:

```bash
gh repo create {{repo_name}} --public --add-readme --clone
```

Example:

```bash
gh repo create demo-to-do-list --public --add-readme --clone
```

This creates the repository, initializes it with `README.md`, sets it public, and clones it locally.

## Set Default Branch to `main`
If the repository default branch is not already `main`, run:

```bash
gh repo edit {{owner}}/{{repo_name}} --default-branch=main
```

Example:

```bash
gh repo edit angelalita77/demo-to-do-list --default-branch=main
```

## Make Repository Public
If the repository needs to be made public explicitly:

```bash
gh repo edit {{owner}}/{{repo_name}} --visibility=public --accept-visibility-change-consequences
```

Example:

```bash
gh repo edit angelalita77/demo-to-do-list --visibility=public --accept-visibility-change-consequences
```

## Confirm the Setup
Check the local clone state:

```bash
cd {{repo_name}}
git branch -a
```

Check the remote repository details:

```bash
gh repo view {{owner}}/{{repo_name}}
```

## Notes
- `--add-readme` initializes the repository with `README.md`.
- Use `main` rather than `master` for the default branch.
- The `gh` CLI may require browser-based authentication the first time it is used.
