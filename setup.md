# career-ops — Personal Setup

Personal fork of [santifer/career-ops](https://github.com/santifer/career-ops).

## Customizations in this fork

| Change | Details |
|--------|---------|
| **English mode files** | `modes/scan.md`, `modes/pdf.md`, `modes/deep.md`, `batch/batch-prompt.md` translated from Spanish |
| **54 tracked companies** | Curated US AI/ML companies with Greenhouse, Ashby, and Lever APIs wired |

---

## When to pull from santifer/career-ops (upstream)

Pull upstream updates when you want bug fixes, new features, or new mode logic — **but only after checking if any translated files changed.**

### Step 1 — Check what upstream changed

```bash
git fetch upstream
git diff HEAD upstream/main -- modes/scan.md modes/pdf.md modes/deep.md modes/auto-pipeline.md modes/contacto.md modes/_shared.md AGENTS.md batch/batch-prompt.md
```

If none of those files changed upstream, it's safe to merge freely.

### Step 2 — Merge upstream

```bash
git merge upstream/main
```

If git reports conflicts on translated mode files, keep **your** version:

```bash
# For each conflicting file, accept your local version
git checkout --ours modes/scan.md
git checkout --ours modes/pdf.md
# ... repeat for each conflicted file
git add modes/scan.md modes/pdf.md  # etc.
git merge --continue
```

### Step 3 — If a translated file changed upstream and you want the update

Review the upstream version, manually merge any new logic into the English translation, then commit.

```bash
# See what santifer changed in a specific file
git show upstream/main:modes/scan.md | diff - modes/scan.md
```

---

## Warning: `node update-system.mjs apply`

The update system fetches directly from `santifer/career-ops` (hardcoded) and **will overwrite translated mode files** regardless of your git state.

- **Decline the update prompt** when Claude asks "Want me to update?" at session start
- If you accidentally apply an update, recover with:
  ```bash
  # The update system creates a backup branch automatically
  git branch | grep backup-pre-update
  git checkout backup-pre-update-<timestamp> -- modes/scan.md modes/pdf.md # etc.
  git commit -m "restore translations after upstream update"
  git push origin main
  ```

---

## Remotes

```
origin    https://github.com/mohitkumar1512/career-ops.git  (your fork)
upstream  https://github.com/santifer/career-ops.git        (original)
```
