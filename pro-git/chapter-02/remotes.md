## Working with Remotes

### Showing Your Remotes

```shell
git remote
```

```shell
git clone git@github.com:schacon/ticgit.git
cd ticgit
git remote
```

```shell
origin
```

We can get more information about a remote by using the `--verbose` option:

```shell
git remote --verbose
```

```shell
origin  git@github.com:schacon/ticgit.git (fetch)
origin  git@github.com:schacon/ticgit.git (push)
```

### Adding Remotes

```shell
git remote add pb git@github.com:paulboone/ticgit
git remote --verbose
```

```shell
origin  git@github.com:schacon/ticgit.git (fetch)
origin  git@github.com:schacon/ticgit.git (push)
pb      git@github.com:paulboone/ticgit (fetch)
pb      git@github.com:paulboone/ticgit (push)
```

### Fetching and Pulling from Your Remotes

Now that we've added `pb` as a shortname to a different remote repository, we can fetch it:

```shell
git fetch pb
```

```shell
remote: Enumerating objects: 43, done.
remote: Counting objects: 100% (22/22), done.
remote: Total 43 (delta 22), reused 22 (delta 22), pack-reused 21 (from 1)
Unpacking objects: 100% (43/43), 5.99 KiB | 58.00 KiB/s, done.
From github.com:paulboone/ticgit
 * [new branch]      master     -> pb/master
 * [new branch]      ticgit     -> pb/ticgit
```

What this does is essentially pulling changes from the `pb` remote repository into our own repository. This includes all branches that `pb` has, but we don't on ours; you can then merge or inspect this changes at any time.

> [!TIP]
>
> - When you a repository is cloned from its remote, the shortname would always be `origin`.
> - The `git fetch` command is used to fetch changes from a remote repository. It doesn't merge the changes into your repository; that would have to be done manually.

### Inspecting a Remote

```shell
git remote show origin
```

```shell
* remote origin
  Fetch URL: git@github.com:schacon/ticgit.git
  Push  URL: git@github.com:schacon/ticgit.git
  HEAD branch: master
  Remote branches:
    master tracked
    ticgit tracked
  Local branch configured for 'git pull':
    master merges with remote master
  Local ref configured for 'git push':
    master pushes to master (up to date)
```

### Renaming and Removing Remotes

Let's rename the shortname `pb` to `paul` with `git remote rename <current> <new>`:

```shell
git remote rename pb paul
```

```shell
Renaming remote references: 100% (2/2), done.
```

```shell
git remote --verbose
```

```shell
origin  git@github.com:schacon/ticgit.git (fetch)
origin  git@github.com:schacon/ticgit.git (push)
paul    git@github.com:paulboone/ticgit (fetch)
paul    git@github.com:paulboone/ticgit (push)
```

If — for whatever reason — you don't want to work with a remote repository anymore, you can remove it with the `git remote remove <shortname>` command:

```shell
git remote remove paul
git remote --verbose
```

```shell
origin  git@github.com:schacon/ticgit.git (fetch)
origin  git@github.com:schacon/ticgit.git (push)
```
