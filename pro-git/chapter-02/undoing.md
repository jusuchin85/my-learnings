## Undoing Things

### Amending the Last Commit

```shell
git commit -m "Initial commit"
git add forgotten_file
git commit --amend
```

> [!IMPORTANT]
>
> - The above command will only work if the forgotten file is not yet staged. If the forgotten file is already staged, you can unstage it with `git reset HEAD <file>` and then commit it with `git commit --amend`.
> - The `--amend` option will only work if you haven't pushed the commit to a remote repository yet. If you have pushed the commit to a remote repository, you will need to force push the amended commit with `git push --force`.

### Unstaging a Staged File

```shell
git add *
git status
```

```shell
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        renamed:    forgotten_file -> CONTRIBUTING.md
        modified:   README.md
```

Let's unstage the `README.md` file:

```shell
git restore --staged README.md
git status
```

```shell
git status                    
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        renamed:    forgotten_file -> CONTRIBUTING.md

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md
```

### Unmodifying a Modified File

Let's undo all the changes made to the `README.md` file:

```shell
git restore README.md
git status
```

```shell
On branch main
Your branch is up to date with 'origin/main'.

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        renamed:    forgotten_file -> CONTRIBUTING.md
```
