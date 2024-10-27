## Compare Changes Made with `git diff`

Use `git status` as a primer for this:

```shell
git status
```

```shell
On branch 2024-10-21_pro-git
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md
        modified:   pro-git/chapter-01/README.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        pro-git/chapter-02/

no changes added to commit (use "git add" and/or "git commit -a")
```

Let's check what was changed in `README.md`:

```shell
git diff README.md
```

```shell
diff --git a/README.md b/README.md
index 74889a8..b4e04ff 100644
--- a/README.md
+++ b/README.md
@@ -6,4 +6,4 @@ Contains a collection of READMEs for the various areas of my learning. Some exer
 
 - [GNU `grep` and `ripgrep`](gnu-grep/)
 - [LDAP](ldap/)
-- [Pro Git](pro-git/)
\ No newline at end of file
+- [Pro Git](pro-git/)
```

## Removing Files from the Staging Area, but Retaining in the Working Directory

```shell
git rm --cached FILENAME
```

This way, the file will no longer be tracked, but you want to retain in the working directory — perhaps to be added to the `.gitignore` file.
