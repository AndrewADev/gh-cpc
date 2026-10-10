# gh-cpc

A `gh` extension that cherry-picks a commit onto a fresh branch from `origin/main`, in its own worktree, pushes it, and optionally opens a PR.

## Install

```sh
gh extension install andrewadev/gh-cpc
```

From a local checkout:

```sh
gh extension install .
```

## Usage

```sh
gh cpc <commit>
```

The branch name is derived from the commit's conventional-commit subject:
`feat(parser): add yaml support` becomes `feat/parser/add-yaml-support`. Other subjects use the `chore/` prefix. The worktree is created at `worktrees/<branch-with-dashes>` in the main checkout.

After pushing, the command prompts whether to open a PR (`gh pr create --fill-first`) and which labels to add.

## Configuration

| Variable         | Default | Description                    |
| ---------------- | ------- | ------------------------------ |
| `GH_CPC_BASE`    | `main`  | Base branch on `origin`        |
| `BRANCH_MAX_LEN` | `60`    | Maximum generated branch length |
