---
name: commit
description: >
  Creates git commits with proper conventional commit messages and GPG signing.
  Use this skill whenever the user wants to commit changes, stage files and commit,
  or asks to "commit this", "create a commit", "save my changes to git", or anything
  involving git commits. Always use conventional commits unless the repository uses
  a different scheme. Never skip GPG signing — commits must always be signed.
disable-model-invocation: false
user-invocable: true
allowed-tools: Bash Glob Grep Read
---

# Commit Skill

Create a well-formed, GPG-signed git commit. Every commit must be signed — unsigned commits are not acceptable.

## Step 1: Understand the repository's commit conventions

Before writing a message, check if the project uses a non-standard commit scheme:

- Read `CONTRIBUTING.md`, `COMMIT_CONVENTION.md`, or similar files if they exist
- Scan recent commits with `git log --oneline -20` to detect the pattern in use

If no established scheme is found, use **Conventional Commits** (see below).

## Step 2: Assess what to commit

Run `git status` and `git diff --staged` (and `git diff` if nothing is staged yet) to understand what changed. If the user didn't specify which files to stage, use your judgment — stage files related to the stated task, and ask if anything is ambiguous.

Do NOT stage:
- `.env` files or anything containing secrets
- Build artifacts or generated files that belong in `.gitignore`
- Unrelated changes the user didn't mention

## Step 3: Write the commit message

**Commit messages must be in English.**

### Conventional Commits format (default)

```
<type>(<scope>): <short summary>

[optional body]

[optional footer]
```

**Types:**
- `feat` — new feature
- `fix` — bug fix
- `docs` — documentation only
- `style` — formatting, no logic change
- `refactor` — restructuring without behavior change
- `test` — adding or updating tests
- `chore` — maintenance, tooling, dependencies
- `perf` — performance improvement
- `ci` — CI/CD changes
- `build` — build system changes

**Rules:**
- Summary line: imperative mood, lowercase after the colon, no period, max 72 chars
- Scope is optional but helpful (e.g., `feat(auth):`, `fix(api):`)
- Body: wrap at 72 chars, explain *why* not *what*
- Breaking changes: add `BREAKING CHANGE:` in footer or `!` after type (`feat!:`)

**Examples:**
```
feat(auth): add JWT token refresh endpoint

fix: handle null pointer in user lookup

docs(readme): update installation instructions

feat!: remove deprecated v1 API endpoints

BREAKING CHANGE: v1 endpoints have been removed. Migrate to v2.
```

## Step 4: Create the signed commit

GPG signing is mandatory. Philipp signs commits interactively using a YubiKey.

```bash
git commit -S -m "$(cat <<'EOF'
<your message here>
EOF
)"
```

The `-S` flag triggers GPG signing. This will prompt for YubiKey interaction (touch or PIN entry) — this is expected and normal.

**If signing fails:**

1. Check the error message carefully
   - `gpg: signing failed: No secret key` → GPG key not available
   - `gpg: signing failed: Timeout` or `Card error` → YubiKey not responding
   - `gpg: signing failed: Operation cancelled` → user cancelled PIN entry
2. Try once more — a single retry is reasonable if it looks like a transient error
3. If it fails again, stop and tell Philipp what went wrong. Do not attempt workarounds, do not use `--no-gpg-sign`, do not proceed without a signature. Ask Philipp to verify their YubiKey is inserted and unlocked, then try again when ready.

## Step 5: Confirm

After a successful commit, show the commit hash and summary:

```bash
git log --oneline -1
```

Tell Philipp what was committed and confirm everything looks right.
