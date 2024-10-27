## Limiting Log Output

> [!TIP]
> More options for `git log` can be found here [^4].

### `git log --since=<n>`

Show the commit history since a specific `<n>` period.:

```shell
git log --since=2.weeks

commit 093115704ed39d8544b42cb0f040da6e96b9f1af (HEAD -> 2024-10-28_pro-git, origin/development, development)
Author: Justin Alex Paramanandan <1155821+jusuchin85@users.noreply.github.com>
Date:   Mon Oct 21 10:59:09 2024 +1100

    2024-10-21: Pro Git Learnings (#3)
    
    * Chapter 01
    * Chapter 02

commit 9540054165b7e2a56d7fe18f5e95216012da9f27
Merge: ed64291 cbf9b53
Author: Justin Alex Paramanandan <1155821+jusuchin85@users.noreply.github.com>
Date:   Mon Oct 21 10:04:12 2024 +1100

    Merge branch 'main' into development

commit cbf9b53ae48e3f8cf8e54432e33b64bd59383b82 (origin/main, origin/HEAD, main)
Author: Justin Alex Paramanandan <1155821+jusuchin85@users.noreply.github.com>
Date:   Mon Oct 21 10:00:33 2024 +1100

    First PR for LDAP (#2)
    
    * Create LDAP directory
        - renamed `commands` directory to `ldapsearch`
        - added README for LDAP directory
...
```

### `git log -S <string>`

Show the commit history with the changes that include the `<string>`:

```shell
git log -S ldapsearch

commit cbf9b53ae48e3f8cf8e54432e33b64bd59383b82 (origin/main, origin/HEAD, main)
Author: Justin Alex Paramanandan <1155821+jusuchin85@users.noreply.github.com>
Date:   Mon Oct 21 10:00:33 2024 +1100

    First PR for LDAP (#2)
    
    * Create LDAP directory
        - renamed `commands` directory to `ldapsearch`
        - added README for LDAP directory
```

### Common options to limit output to `git-log`

- `-<n>`: Show only the last `n` commits.
- `--since`, `--after`: Limit the commits to those made after the specified date.
- `--until`, `--before`: Limit the commits to those made before the specified date.
- `--author`: Only show commits in which the author entry matches the specified string.
- `--committer`: Only show commits in which the committer entry matches the specified string.
- `-S`: Only show commits adding or removing the specified string.
- `--grep`: Only show commits whose message matches the specified regular expression.

For example, to see commits in the Git repository [^1] that:

- were modified test files
- committed by Junio C Hamano
- committed in the month of October 2008
- not merge commits

```shell
git log --pretty=format:"%h - %an, %ad : %s" --author="Junio C Hamano" --since="2008-10-01" --before="2008-11-01" --no-merges -- t/

5610e3b031 - Junio C Hamano, Sun Oct 19 22:51:17 2008 -0700 : Fix testcase failure when extended attributes are in use
acd3b9eca8 - Junio C Hamano, Fri Oct 17 15:44:39 2008 -0700 : Enhance hold_lock_file_for_{update,append}() API
f5637549a7 - Junio C Hamano, Fri Oct 17 15:56:11 2008 -0700 : demonstrate breakage of detached checkout with symbolic link HEAD
d1a43f2aa4 - Junio C Hamano, Wed Oct 15 16:00:06 2008 -0700 : reset --hard/read-tree --reset -u: remove unmerged new paths
51a94af845 - Junio C Hamano, Thu Oct 16 23:37:44 2008 -0700 : Fix "checkout --track -b newbranch" on detached HEAD
b0ad11ea16 - Junio C Hamano, Tue Oct 14 15:32:20 2008 -0700 : pull: allow "git pull origin $something:$current_branch" into an unborn branch
```

At time of writing, there are more than 75,000 commits in the Git source code history. This command shows the 6 commits that match the specified criteria.

[^1]: [Git repository](https://github.com/git/git)
