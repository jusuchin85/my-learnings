## Checking Commit History

> [!TIP]
> More options for `git log` can be found here [^1].

### `git log`

Show the commit history:

```shell
commit ca82a6dff817ec66f44342007202690a93763949 (HEAD -> master, origin/master, origin/HEAD)
Author: Scott Chacon <schacon@gmail.com>
Date:   Mon Mar 17 21:52:11 2008 -0700

    changed the verison number

commit 085bb3bcb608e1e8451d4b2432f8ecbe6306e7e7
Author: Scott Chacon <schacon@gmail.com>
Date:   Sat Mar 15 16:40:33 2008 -0700

    removed unnecessary test code

commit a11bef06a3f659402fe7563abf99ad00de2209e6
Author: Scott Chacon <schacon@gmail.com>
Date:   Sat Mar 15 10:31:28 2008 -0700

    first commit
```

### `git log --patch -<n>`

Show the commit history with the diff of each commit (with `<n>` being the last `n` entries to show):

```shell
commit ca82a6dff817ec66f44342007202690a93763949 (HEAD -> master, origin/master, origin/HEAD)
Author: Scott Chacon <schacon@gmail.com>
Date:   Mon Mar 17 21:52:11 2008 -0700

    changed the verison number

diff --git a/Rakefile b/Rakefile
index a874b73..8f94139 100644
--- a/Rakefile
+++ b/Rakefile
@@ -5,7 +5,7 @@ require 'rake/gempackagetask'
 spec = Gem::Specification.new do |s|
     s.platform  =   Gem::Platform::RUBY
     s.name      =   "simplegit"
-    s.version   =   "0.1.0"
+    s.version   =   "0.1.1"
     s.author    =   "Scott Chacon"
     s.email     =   "schacon@gmail.com"
     s.summary   =   "A simple gem for using Git in Ruby code."

commit 085bb3bcb608e1e8451d4b2432f8ecbe6306e7e7
Author: Scott Chacon <schacon@gmail.com>
Date:   Sat Mar 15 16:40:33 2008 -0700

    removed unnecessary test code

diff --git a/lib/simplegit.rb b/lib/simplegit.rb
index a0a60ae..47c6340 100644
--- a/lib/simplegit.rb
+++ b/lib/simplegit.rb
@@ -18,8 +18,3 @@ class SimpleGit
     end

 end
-
-if $0 == __FILE__
-  git = SimpleGit.new
-  puts git.show
-end
```

### `git log --stat`

Show the commit history with the number of insertions and deletions in each commit:

```shell
commit ca82a6dff817ec66f44342007202690a93763949 (HEAD -> master, origin/master, origin/HEAD)
Author: Scott Chacon <schacon@gmail.com>
Date:   Mon Mar 17 21:52:11 2008 -0700

    changed the verison number

 Rakefile | 2 +-
 1 file changed, 1 insertion(+), 1 deletion(-)

commit 085bb3bcb608e1e8451d4b2432f8ecbe6306e7e7
Author: Scott Chacon <schacon@gmail.com>
Date:   Sat Mar 15 16:40:33 2008 -0700

    removed unnecessary test code

 lib/simplegit.rb | 5 -----
 1 file changed, 5 deletions(-)

commit a11bef06a3f659402fe7563abf99ad00de2209e6
Author: Scott Chacon <schacon@gmail.com>
Date:   Sat Mar 15 10:31:28 2008 -0700

    first commit

 README           |  6 ++++++
 Rakefile         | 23 +++++++++++++++++++++++
 lib/simplegit.rb | 25 +++++++++++++++++++++++++
 3 files changed, 54 insertions(+)
```

### `git log --pretty=<option>`

Show the commit history in one line. Options include:

- `oneline`: show the commit hash and the commit message in one line

    ```shell
    git log --pretty=oneline

    ca82a6dff817ec66f44342007202690a93763949 (HEAD -> master, origin/master, origin/HEAD) changed the verison number
    085bb3bcb608e1e8451d4b2432f8ecbe6306e7e7 removed unnecessary test code
    a11bef06a3f659402fe7563abf99ad00de2209e6 first commit
    ```

- `format:"%h - %an, %ar : %s"`: show the abbreviated commit hash (`%h`), the author name (`%an`), the author date, relative (`%ar`), and the subject (`%s`) of the commit

    ```shell
    git log git log --pretty=format:"%h - %an, %ad : %s"

    ca82a6d - Scott Chacon, 7 years ago : changed the verison number
    085bb3b - Scott Chacon, 7 years ago : removed unnecessary test code
    a11bef0 - Scott Chacon, 7 years ago : first commit
    ```

## Combining the `--pretty` option with the `--graph` option

Combining both the `--pretty` and `--graph` options will show the commit history in a graph format. Below is an example of the commit history of this repository:

```shell
git log --pretty=format:"%h %s" --graph

* 0931157 2024-10-21: Pro Git Learnings (#3)
*   9540054 Merge branch 'main' into development
|\  
| * cbf9b53 First PR for LDAP (#2)
* | ed64291 First PR for `gnu grep` (#1)
|/  
* fe49b8b Initial commit
```

### Common options to `git-log`

- `-p` or `--patch`: Show the patch introduced with each commit.
- `--stat`: Show statistics for files modified in each commit.
- `--shortstat`: Show only the changed/insertions/deletions line from the `--stat` option.
- `--name-only`: Show the list of files modified after the commit information.
- `--name-status`: Show the list of files modified after the commit information, indicating the status of the changes.
- `--abbrev-commit`: Show only the first few characters of the SHA-1 checksum instead of all 40.
- `--relative-date`: Display the date in a relative format (e.g. "2 weeks ago") instead of using the full date format.
- `--graph`: Show an ASCII graph of the branch and merge history beside the log output.
- `--pretty`: Show commits in an alternate format. Options include `oneline`, `short`, `full`, `fuller`, `format`, and `email`.
- `--oneline`: Shorthand for `--pretty=oneline --abbrev-commit` used together.

[^1]: [Manual for `git-log`](https://git-scm.com/docs/git-log)
