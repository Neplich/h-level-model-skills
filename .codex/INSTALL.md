# Installing H-Level Model Skills for Codex

Install this repository into Codex with a hidden mirror and root-level relative
skill symlinks. Use the installer to maintain those relative symlinks.

## Installation Scope

Use the installation scope specified by the user or established in context. If it is unresolved, ask whether the skills should be available in this project or across projects.

The install includes all eight skills across four plugin categories. Every skill is directly usable. The assistant selects relevant methods for the user's goal and continues within existing authorization.

## Mirror Layout

Codex resolves skill symlinks to their real paths when discovering plugin metadata. The repository keeps `agents/{role}/.claude-plugin/plugin.json` files for Claude marketplace compatibility.

The installer copies the `agents/` tree into `$SKILL_ROOT/.h-level-model-skills/`, with professional references included and plugin manifests and test directories excluded. It creates relative symlinks such as `$SKILL_ROOT/human-writing -> .h-level-model-skills/agents/product_manager/skills/human-writing`. This layout exposes each skill once under its own name and preserves relative references.

## Installation Steps

### 1. Resolve Paths

For a personal install:

```bash
CLONE_ROOT="$HOME/.agents/h-level-model-skills"
SKILL_ROOT="$HOME/.agents/skills"
```

A personal install makes the skills discoverable across projects. A project install keeps them inside the selected project. Skills are selected according to the task or by explicit name.

For a project install, run from the project root:

```bash
PROJECT_ROOT="$PWD"
CLONE_ROOT="$PROJECT_ROOT/.agents/h-level-model-skills"
SKILL_ROOT="$PROJECT_ROOT/.agents/skills"
```

### 2. Clone Or Update The Repository

Set `TARGET_TAG` to a release tag (only when that tag exists in this repository) when this install
must match a specific released version, as the Release upgrade instructions
do. Omit it for a plain latest install.

```bash
REPO_URL="https://github.com/Neplich/h-level-model-skills.git"
if [ -d "$CLONE_ROOT/.git" ]; then
  if [ -n "$(git -C "$CLONE_ROOT" status --porcelain)" ]; then
    echo "error: $CLONE_ROOT has uncommitted or untracked changes; commit or stash them before installing" >&2
    exit 1
  fi
  if [ -n "${TARGET_TAG:-}" ]; then
    git ls-remote --exit-code --tags "$REPO_URL" "refs/tags/${TARGET_TAG}" >/dev/null \
      || { echo "error: release tag $TARGET_TAG not found on origin; aborting pinned install" >&2; exit 1; }
    # Fetch from the verified URL into the local tag ref so the checkout and
    # identity checks read the official object.
    git -C "$CLONE_ROOT" fetch "$REPO_URL" "refs/tags/${TARGET_TAG}:refs/tags/${TARGET_TAG}" \
      || { echo "error: fetch failed; aborting pinned install" >&2; exit 1; }
    git -C "$CLONE_ROOT" checkout --detach "refs/tags/${TARGET_TAG}^{commit}" \
      || { echo "error: cannot checkout $TARGET_TAG; aborting pinned install" >&2; exit 1; }
    test "$(git -C "$CLONE_ROOT" rev-parse HEAD)" = "$(git -C "$CLONE_ROOT" rev-parse "refs/tags/${TARGET_TAG}^{commit}")" \
      || { echo "error: checkout verification failed for $TARGET_TAG; aborting pinned install" >&2; exit 1; }
  else
    # A previous pinned install leaves a detached HEAD; return to main first
    # so the unpinned update applies to main.
    git -C "$CLONE_ROOT" checkout main || { echo "error: cannot switch to main; aborting update" >&2; exit 1; }
    git -C "$CLONE_ROOT" pull --ff-only || { echo "error: update failed; aborting install" >&2; exit 1; }
  fi
else
  mkdir -p "$(dirname "$CLONE_ROOT")"
  if [ -n "${TARGET_TAG:-}" ]; then
    git ls-remote --exit-code --tags "$REPO_URL" "refs/tags/${TARGET_TAG}" >/dev/null \
      || { echo "error: release tag $TARGET_TAG not found on origin; aborting pinned install" >&2; exit 1; }
    git clone "$REPO_URL" "$CLONE_ROOT"
    git -C "$CLONE_ROOT" checkout --detach "refs/tags/${TARGET_TAG}^{commit}" \
      || { echo "error: cannot checkout $TARGET_TAG; aborting pinned install" >&2; exit 1; }
    test "$(git -C "$CLONE_ROOT" rev-parse HEAD)" = "$(git -C "$CLONE_ROOT" rev-parse "refs/tags/${TARGET_TAG}^{commit}")" \
      || { echo "error: checkout verification failed for $TARGET_TAG; aborting pinned install" >&2; exit 1; }
  else
    git clone "$REPO_URL" "$CLONE_ROOT"
  fi
fi
```

### 3. Install Skills

Default all skills:

```bash
python3 "$CLONE_ROOT/scripts/install_codex_skills.py" --target "$SKILL_ROOT"
```

The installer manages its own marker-bearing hidden mirror and symlinks resolving
inside that mirror. Unregistered aliases pointing into this mirror are removed
on update. Legacy aggregate entries are migrated only when marked as owned.
Symlinks into other checkouts or the original dev-agent-skills mirror are
unowned and preserved. Installing this library does not uninstall the original.

Real directories and symlinks to other locations are preserved and reported as skipped. With `--force`, they are reported as
conflicts and the installer exits before rebuilding the mirror or changing any
target entries. Use `--force` to rebuild the hidden mirror and replace all owned
symlinks:

```bash
python3 "$CLONE_ROOT/scripts/install_codex_skills.py" --target "$SKILL_ROOT" --force
```

The installer prints the installed, updated, migrated, replaced, or skipped
skills and warns if the target ancestor chain contains
`.claude-plugin/plugin.json` or `.codex-plugin/plugin.json`.

## Disable One Skill By Path

To keep an installed skill on disk but hide it from Codex, add a path-specific entry
to `~/.codex/config.toml`:

```toml
[[skills.config]]
path = "/Users/you/.agents/skills/e2e-testing"
enabled = false
```

Use the visible target-root symlink path on the user's machine.
