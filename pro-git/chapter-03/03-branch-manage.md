# Branch Management

## Viewing merged and unmerged branches

To view branches that have merged into the checked-out branch:

```shell
$ git branch --merged

  hotfix-2
  iss54
* main
```

To view branches that have not been merged into the current branch:

```shell
$ git branch --no-merged

  testing
```

A branch name can be passed to the `--no-merged` option to view branches that have yet to be merged into the specified branch (without switching to that branch):

```shell

## What branch am I currently on?

$ git branch

* 2025-02_pro-git
  development
  gnu-grep-ripgrep
  main

---

## What branches are not merged into the main branch?

$ git branch --no-merged main

* 2025-02_pro-git
  development

```

## Changing a branch name

TODO: continue on 2025-02-24
