- [Tagging](#tagging)
  - [Listing your Tags](#listing-your-tags)
  - [Creating Tags](#creating-tags)
    - [Annotated tags](#annotated-tags)
    - [Lightweight tags](#lightweight-tags)
  - [Tagging Later](#tagging-later)
  - [Sharing Tags](#sharing-tags)
    - [To push a specific tag to a remote repository](#to-push-a-specific-tag-to-a-remote-repository)
    - [To push all tags to a remote repository (in cases where there are a lot of tags to push manually)](#to-push-all-tags-to-a-remote-repository-in-cases-where-there-are-a-lot-of-tags-to-push-manually)
  - [Deleting Tags](#deleting-tags)
  - [Checking out Tags](#checking-out-tags)

## Tagging

### Listing your Tags

Let's run the following command to list the tags in the `git` repository:

```shell
git tag | head -n 2
```

```shell
gitgui-0.10.0
gitgui-0.10.1
```

The `git` repository contains more than 900 tags. If you want to limit your tag list to the `1.8.5` series, you can run the following command:

```shell
git tag --list 'v1.8.5*'
```

```shell
v1.8.5
v1.8.5-rc0
v1.8.5-rc1
v1.8.5-rc2
v1.8.5-rc3
v1.8.5.1
v1.8.5.2
v1.8.5.3
v1.8.5.4
v1.8.5.5
v1.8.5.6
```

### Creating Tags

There are two types of tags in `git`: _lightweight_ and _annotated_.

- A lightweight tag is very much like a branch that doesn't change. It's just a pointer to a specific commit.
- Annotated tags, however, are stored as full objects in the `git` database. They're checksummed; contain the tagger name, email, and date; have a tagging message; and can be signed and verified with GNU Privacy Guard (GPG). It's generally recommended that you create annotated tags so you can have all this information; but if you want a temporary tag or for some reason don't want to keep the other information, you can create lightweight tags with the `-a` option:

#### Annotated tags

To create an annotated tag in `git`, you can run the following command:

```shell
git tag --annotate v1.4 --message "My version 1.4"
git tag
```

```shell
v1.4
```

We passed in the `--message` option to provide a tagging message. In order to view the tag data that is stored in the `git` database, you can run the following command:

```shell
git show v1.4
```

```shell
tag v1.4
Tagger: Justin Alex Paramanandan <1155821+jusuchin85@users.noreply.github.com>
Date:   Mon Nov 11 10:42:30 2024 +1100

My version 1.4

commit 05c9df45d270b2a83a3733b6334a36f35077ec5f (HEAD -> main, tag: v1.4, origin/main)
Author: Justin Alex Paramanandan <1155821+jusuchin85@users.noreply.github.com>
Date:   Mon Nov 11 10:17:12 2024 +1100

    Pushing latest updates
```

The `git show` command displays the tag data, the commit that was tagged, and the commit data.

#### Lightweight tags

Lightweight tags are created by running the following command:

```shell
git tag v1.4-lw
git tag
```

```shell
v1.4
v1.4-lw
```

Now if you run the `git show` command to view the tag data, you won't see the extra tag information:

```shell
git show v1.4-lw
```

```shell
commit 05c9df45d270b2a83a3733b6334a36f35077ec5f (HEAD -> main, tag: v1.4-lw, tag: v1.4, origin/main)
Author: Justin Alex Paramanandan <1155821+jusuchin85@users.noreply.github.com>
Date:   Mon Nov 11 10:17:12 2024 +1100

    Pushing latest updates
```

### Tagging Later

If you forgot to tag a commit, you can tag it later. Let's view the commit history for this repository:

```shell
git log --pretty=oneline
```

```shell
05c9df45d270b2a83a3733b6334a36f35077ec5f (HEAD -> main, tag: v1.4-lw, tag: v1.4, origin/main) Pushing latest updates
093b2f8f79255740a393ac72f28559454c077194 Initial commit
```

The `093b2f8` commit is the initial commit, and we forgot to tag it. To tag this commit, you can run the following command:

```shell
git tag --annotate v1.0 093b2f8
git tag
```

```shell
v1.0
v1.4
v1.4-lw
```

```shell
git show v1.0
```

```shell
tag v1.0
Tagger: Justin Alex Paramanandan <1155821+jusuchin85@users.noreply.github.com>
Date:   Mon Nov 11 10:49:33 2024 +1100

This is the initial tag

commit 093b2f8f79255740a393ac72f28559454c077194 (tag: v1.0)
Author: Justin Alex Paramanandan <1155821+jusuchin85@users.noreply.github.com>
Date:   Mon Nov 11 10:05:14 2024 +1100

    Initial commit
    
    Together with forgotten_file
```

### Sharing Tags

Run `git tag` to show existing tags:

```shell
git tag
```

```shell
v1.0
v1.4
v1.4-lw
```

#### To push a specific tag to a remote repository

```shell
git push origin <tag>
```

```shell
git push origin v1.4

Enumerating objects: 1, done.
Counting objects: 100% (1/1), done.
Writing objects: 100% (1/1), 225 bytes | 225.00 KiB/s, done.
Total 1 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To github.com:jusuchin85/fuzzy-waffle.git
 * [new tag]         v1.4 -> v1.4
```

#### To push all tags to a remote repository (in cases where there are a lot of tags to push manually)

```shell
git push origin --tags
```

```shell
Enumerating objects: 1, done.
Counting objects: 100% (1/1), done.
Writing objects: 100% (1/1), 234 bytes | 234.00 KiB/s, done.
Total 1 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To github.com:jusuchin85/fuzzy-waffle.git
 * [new tag]         v1.0 -> v1.0
 * [new tag]         v1.4-lw -> v1.4-lw
```

> [!NOTE]
> `git push <remote> --tags` will push all of your tags — both lightweight and annotated — to a remote repository. If you don't want to push your lightweight tags, you can use the `--follow-tags` option to only push annotated tags.

### Deleting Tags

To delete a tag, you can run the `git tag --delete <tag>` command:

```shell
git tag --delete v1.4-lw

Deleted tag 'v1.4-lw' (was 05c9df4)
```

This only deletes the tag on your local repository. To delete the tag on the remote repository, use the `git push origin --delete <tag>` command:

```shell
git push origin --delete v1.4-lw

To github.com:jusuchin85/fuzzy-waffle.git
 - [deleted]         v1.4-lw
```

### Checking out Tags

Checking out tags is similar to switching a branch (using the `git checkout <tag>` command); though this would place your repository in a "detached HEAD" state. This is because you will be checking out a specific commit, and not a branch. To check out a tag, you can run the following command:

```shell
git checkout v1.0
```

```shell
Note: switching to 'v1.0'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 093b2f8 Initial commit
```

This workflow is not typically executed, unless in circumstances where you want to raise a commit against the specific version (like a hotfix). In such cases, you can create a new branch from the tag and raise your commit there:

```shell
git checkout -b <branch> <tag>

Switched to a new branch 'hotfix-1.0'
```
