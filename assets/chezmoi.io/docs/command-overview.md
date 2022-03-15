# Command overview

## Getting started

* `chezmoi doctor` checks for common problems. If you encounter something unexpected, run this first.

* `chezmoi init` creates chezmoi's source directory and a git repo on a new machine.

## Daily commands

* `chezmoi add <file>` adds `<file>`from your home directory to the source directory.

* `chezmoi edit <file>` opens your editor with the file in the source directory that corresponds to `<file>`.

* `chezmoi status` gives a quick summary of what files would change if you ran `chezmoi apply`.

* `chezmoi diff` shows the exact changes that `chezmoi apply` would make to your home directory.

* `chezmoi apply` updates your dotfiles from the source directory.

* `chezmoi edit --apply <file>` is like `chezmoi edit <file>` but also runs `chezmoi apply <file>` afterwards.

```mermaid
sequenceDiagram
    participant H as home directory
    participant W as working copy
    participant L as local repo
    participant R as remote repo
    H->>W: chezmoi add &lt;file&gt;
    W->>W: chezmoi edit &lt;file&gt;
    W-->>H: chezmoi status
    W-->>H: chezmoi diff
    W->>H: chezmoi apply
    W->>H: chezmoi edit --apply &lt;file&gt;
```

## Using chezmoi across multiple machines

* `chezmoi init <github-username>` clones your dotfiles from GitHub into the source directory.

* `chezmoi init --apply <github-username>` clones your dotfiles from GitHub into the source directory and runs `chezmoi apply`.

* `chezmoi update` pulls the latest changes from your remote repo and runs `chezmoi apply`.

```mermaid
sequenceDiagram
    participant H as home directory
    participant W as working copy
    participant L as local repo
    participant R as remote repo
    R->>W: chezmoi init &lt;github-username&gt;
    R->>H: chezmoi init --apply &lt;github-username&gt;
    R->>H: chezmoi update &lt;github-username&gt;
```
