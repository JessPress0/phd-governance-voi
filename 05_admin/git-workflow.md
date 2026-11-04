# Git workflow — personal reference

Project: `phd-governance-voi` (private)
GitHub: `github.com/JessPress0/phd-governance-voi`
Local:  `~/research/phd-governance-voi` (or wherever you cloned it)

If you are reading this on a new machine, or setting up a new repo,
start at "One-time setup". If you just want the daily loop, skip to
"Everyday workflow".

---

## One-time setup (new machine or new repo)

### 1. Install
- Git (`git --version` should work)
- R + RStudio
- Zotero + Better BibTeX

### 2. Set your identity (once per machine)
    git config --global user.name  "Jessica Presso"
    git config --global user.email "pressojessica@gmail.com"

Change the email if your GitHub account changes. To use a different
email in one specific repo only (without `--global`):

    cd <repo-folder>
    git config user.email "other@example.com"

### 3. Create an SSH key (once per machine)
    ssh-keygen -t ed25519 -C "pressojessica@gmail.com"
    # Press Enter (default path)
    # Enter passphrase twice (or Enter twice for none)

Then add the public key to GitHub:

    cat ~/.ssh/id_ed25519.pub
    # Copy the whole line

GitHub → Settings → SSH and GPG keys → New SSH key → paste → save.

Test:

    ssh -T git@github.com
    # Expect: "Hi JessPress0! You've successfully authenticated..."

### 4. Clone the repo (new machine)
    mkdir -p ~/research
    cd ~/research
    git clone git@github.com:JessPress0/phd-governance-voi.git
    cd phd-governance-voi

Open in RStudio via the `.Rproj` file. In the R console:

    renv::restore()

### 5. Create a new repo (if starting from scratch)
- On GitHub: New repository → private → **do not** tick README /
  .gitignore / license.
- Locally:

      cd <new-folder>
      git init -b main
      git add .
      git commit -m "Initial commit"
      git remote add origin git@github.com:JessPress0/<repo-name>.git
      git push -u origin main

---

## Everyday workflow

Three commands, repeated as you work:

    git add .
    git commit -m "Short description of what changed"
    git push

That's it. Everything else is for when something goes wrong.

### Before pushing, glance at what you're about to send
    git status           # files changed, staged vs not
    git diff             # line-by-line changes (not staged)
    git diff --staged    # changes already added
    git log --oneline    # recent commits

### If you only want to stage some files
    git add README.md 02_math/notation.md
    # (rather than `git add .`)

### If you want to stage parts of a file (advanced)
    git add -p
    # y / n per hunk

---

## Commit messages

Convention (plain, imperative, short):

    Add notation table
    Fix EVPI_G_det boundary case
    Draft Chapter 1 intro
    Update references.bib

Rules of thumb:
- First line ≤ 72 characters, no full stop.
- Imperative mood ("Add", not "Added" or "Adds").
- One logical change per commit. Don't mix "add code + fix typo in README".
- If you need a longer explanation, leave a blank line and write a
  paragraph below the first line.

---

## What to change where

### Change your email (globally)
    git config --global user.email "new@qut.edu.au"
    # Only affects future commits. To re-stamp the most recent one:
    git commit --amend --reset-author --no-edit
    # If already pushed:
    git push --force-with-lease

### Change the remote URL (repo moved / renamed / typo)
    git remote -v                              # see current
    git remote set-url origin git@github.com:JessPress0/NEW-NAME.git
    # Note: `set-url`, not `add` (add refuses if origin exists)

### Change the remote from SSH to HTTPS (fallback)
    git remote set-url origin https://github.com/JessPress0/phd-governance-voi.git
    # On push it will ask for username + personal access token.
    # Generate token: GitHub → Settings → Developer settings →
    #   Personal access tokens → Fine-grained → Contents: RW.

### Rename a branch
    git branch -m new-name
    git push -u origin new-name

### Add a second remote (e.g., a fork or QUT mirror)
    git remote add qut git@github.com:QUT-org/phd-governance-voi.git
    git push qut main

---

## Undoing things

### Undo unstaged changes to a file
    git restore <file>

### Unstage a file (keep the edit)
    git restore --staged <file>

### Undo the last commit (keep the changes)
    git reset --soft HEAD~1

### Undo the last commit AND discard the changes (careful)
    git reset --hard HEAD~1

### Recover a deleted file (not yet committed)
    git restore <file>

### Recover a deleted file (already committed)
    git log --oneline -- <file>                # find the last good commit
    git checkout <commit-hash> -- <file>

### Rename a file
    git mv old/path new/path
    git commit -m "Rename X to Y"

### Delete a file
    git rm path/to/file
    git commit -m "Remove X"

---

## Common errors and fixes

| Error | Cause | Fix |
|---|---|---|
| `Repository not found` | Wrong URL or repo doesn't exist on GitHub | Check the URL with `git remote -v`; open the repo in a browser |
| `Permission denied (publickey)` | SSH key not registered, or agent not running | `ssh -T git@github.com` to test; add key at GitHub → Settings → SSH keys |
| `Updates were rejected... non-fast-forward` | GitHub has commits you don't have locally | `git pull --rebase` then `git push` |
| `nothing to commit, working tree clean` | No changes since last commit | Not an error — you're up to date |
| `fatal: not a git repository` | You're not in the project folder | `cd ~/research/phd-governance-voi` |
| `.DS_Store` shows in `git status` | `.gitignore` not catching it | `cat .gitignore` — must contain `.DS_Store` |
| `error: pathspec 'X' did not match` | File doesn't exist, or wrong case | `ls` to check exact name (macOS is case-insensitive but Git isn't) |
| `Enter passphrase for key ...` on every push | Passphrase not cached | `eval "$(ssh-agent -s)" && ssh-add --apple-use-keychain ~/.ssh/id_ed25519` |

---

## Checking that the repo is clean

    git status                   # "nothing to commit, working tree clean"
    git log --oneline -5         # last 5 commits
    git remote -v                # correct remote?
    git ls-files | head -20      # what's actually tracked

Anything with `.DS_Store`, `renv/library/`, `.Rproj.user/` in
`git ls-files` means a `.gitignore` fix didn't take and those files
got committed. Remove them:

    git rm -r --cached .DS_Store renv/library .Rproj.user
    git commit -m "Untrack ignored files"

---

## Golden rules

1. **Commit early, commit often.** Small commits are easier to undo.
2. **Push at end of every work session.** Backup is the point.
3. **Never force-push** (`git push --force`) unless you know what
   you're doing. Use `--force-with-lease` if you must.
4. **Never commit secrets** — `.env`, tokens, credentials.
5. **Don't commit `renv/library/`, `.DS_Store`, `.Rproj.user/`.**
6. **One concern per commit.** Don't mix "add code" with "fix typo
   in unrelated file".
7. **If lost, `git status` first.** Git almost always tells you
   what the next step is.