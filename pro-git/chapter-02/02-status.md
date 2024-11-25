## More on the `git status` Command

- `git status`: Show the status of changes as untracked, modified, or staged.

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

- Shorter `git status`:

    ```shell
    git status --short
    ```

    ```shell
     M README.md
     M pro-git/chapter-01/README.md
    ?? pro-git/chapter-02/
    ```

  - the first column represents the status of the staging area[^1]
  - the second column represents the status of the working directory[^1]

[^1]: [See Chapter 01](../chapter-01/README.md) for more information on the staging area and the working directory.
