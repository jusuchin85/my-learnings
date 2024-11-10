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

Now if you run the `git show` command to view the tag data, you'll don't see the extra tag information:

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

TODO: TBC
