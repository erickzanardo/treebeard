# treebeard

A shell function for managing git worktrees across projects. Worktrees are stored under `~/.treebeard/<repo>/<name>`, keeping them organized and out of your project directories.

## Installation

1. Clone or download this repository.
2. Add the following line to your `~/.bashrc` or `~/.zshrc`:

```sh
source /path/to/treebeard/treebeard
```

3. Reload your shell:

```sh
source ~/.bashrc   # or source ~/.zshrc
```

## Commands

### `treebeard new <name>`

Creates a new git worktree for the current repository, checked out on a new branch named `<name>`.

Must be run from inside a git repository.

```sh
cd ~/projects/myrepo
treebeard new my-feature
# Created worktree at ~/.treebeard/myrepo/my-feature
```

### `treebeard list`

Lists all worktrees managed by treebeard, grouped by repository.

```sh
treebeard list
# myrepo/my-feature
# myrepo/other-branch
# otherrepo/fix-bug
```

### `treebeard cd <repo>/<name>`

Changes the current directory to the specified worktree.

```sh
treebeard cd myrepo/my-feature
```

### `treebeard cp <repo>/<name> <file>`

Copies a file into the specified worktree directory.

```sh
treebeard cp myrepo/my-feature ./config.json
```

### `treebeard mv <repo>/<name> <file>`

Moves a file into the specified worktree directory.

```sh
treebeard mv myrepo/my-feature ./config.json
```

## How it works

Worktrees are stored at `~/.treebeard/<repo>/<name>`. The repo name is derived automatically from the root of the current git repository. This keeps worktrees centralized and separate from the original project directories.
