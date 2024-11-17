- [Ignoring Files](#ignoring-files)
  - [Glob patterns](#glob-patterns)
  - [Example `.gitignore` file\[^2\]](#example-gitignore-file2)

## Ignoring Files

Rules of `.gitignore` files:

- Blank lines or lines starting with `#` are ignored.
- Standard [glob patterns](#glob-patterns) work, and will be applied recursively throughout the entire working directory (e.g. `*.log`).
- You can start patterns with a forward slash (`/`) to avoid recursivity (e.g. `/*.log`).
- You can end patterns with a forward slash (`/`) to specify a directory (e.g. `log/`).
- You can negate a pattern by starting it with an exclamation point (`!`).

### Glob patterns

Glob patterns are regex[^1] for shell environments. Here are some examples:

- `*`: matches zero or more characters
- `[abc]`: matches any of the characters a, b, or c
- `?`: matches a single character
- brackets enclosing characters separated by a hyphen (`-`) represent a range (e.g. `[1-5]` matches any digit from 1 to 5)
- two asterisks (`**`) represent any number of directories (e.g. `a/**/z` matches `a/z`, `a/b/z`, `a/b/c/z`, etc.)

### Example `.gitignore` file[^2]

```gitignore
# ignore all .a files
*.a

# but do track lib.a, even though you're ignoring .a files above
!lib.a

# only ignore the TODO file in the current directory, not subdir/TODO
/TODO

# ignore all files in any directory named build
build/

# ignore doc/notes.txt, but not doc/server/arch.txt
doc/*.txt

# ignore all .pdf file in the doc/ directory and any of its subdirectories
doc/**/*.pdf
```

[^1]: Regular expressions
[^2]: [Examples from GitHub](https://github.com/github/gitignore)
