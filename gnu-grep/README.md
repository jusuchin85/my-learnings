# GNU grep

> Learnings from [GNU GREP and RIPGREP](https://learnbyexample.gumroad.com/l/gnugrep_ripgrep?layout=profile) by [Sundeep Agarwal](https://learnbyexample.gumroad.com/)

## Exercises

- [Chapter 2](exercises/chapter_2/README.md)

## Simple commands

> Example file: [`programming_quotes.txt`](https://github.com/learnbyexample/learn_gnugrep_ripgrep/blob/master/example_files/freq_options/programming_quotes.txt)

| Criteria                                           |                      `grep` Command                      |                             Manual Reference                            |
|----------------------------------------------------|:--------------------------------------------------------:|:-----------------------------------------------------------------------:|
| Find a word from a text file                       | `grep '[keyword]' [file]`                                | [Link](https://www.gnu.org/software/grep/manual/grep.html)              |
| Regex pattern matching                             | `grep -F '[regex_pattern]' [file]`                       | [Link](https://www.gnu.org/software/grep/manual/grep.html#index-_002dF) |
| Case-insensitive searching                         | `grep -i '[keyword]' [file]`                             | [Link](https://www.gnu.org/software/grep/manual/grep.html#index-_002di) |
| Inverse matching (ignore lines)                    | `grep -v '[keyword]' [file]`                             | [Link](https://www.gnu.org/software/grep/manual/grep.html#index-_002dv) |
| Line number                                        | `grep -n '[keyword]' [file]`                             | [Link](https://www.gnu.org/software/grep/manual/grep.html#index-_002dn) |
| Line count                                         | `grep -c '[keyword]' [file]`                             | [Link](https://www.gnu.org/software/grep/manual/grep.html#index-_002dc) |
| Limit output lines                                 | `grep -m[lines] '[keyword]' [file]`                      | [Link](https://www.gnu.org/software/grep/manual/grep.html#index-_002dm) |
| Search multiple strings                            | `grep -e '[first_keyword]' -e '[second_keyword]' [file]` | [Link](https://www.gnu.org/software/grep/manual/grep.html#index-_002de) |
| Search multiple strings (keywords from a file)     | `grep -f [keyword_file] [file]`                          | [Link](https://www.gnu.org/software/grep/manual/grep.html#index-_002df) |
| List files matching the pattern                    | `grep -l '[keyword]' [file1] [file2]`                    | [Link](https://www.gnu.org/software/grep/manual/grep.html#index-_002dl) |
| List files NOT matching the pattern                | `grep -L '[keyword]' [file1] [file2]`                    | [Link](https://www.gnu.org/software/grep/manual/grep.html#index-_002dL) |
| Suppress filename output (default for single file) | `grep -h '[keyword]' [file1] [file2]`                    | [Link](https://www.gnu.org/software/grep/manual/grep.html#index-_002dh) |
| Show filename output (default for multiple files)  | `grep -H '[keyword]' [file]`                             | [Link](https://www.gnu.org/software/grep/manual/grep.html#index-_002dH) |
| Match whole word only                              | `grep -w '[keyword]' [file]`                             | [Link](https://www.gnu.org/software/grep/manual/grep.html#index-_002dw) |
| Output exact match                                 | `grep -x '[keyword]' [file]`                             | [Link](https://www.gnu.org/software/grep/manual/grep.html#index-_002dx) |
| Common lines between two files                     | `grep -Fxf [file1] [file2]`                              |                                                                         |
| Extract only matching pattern                      | `grep -o '[keyword]' [file]`                             | [Link](https://www.gnu.org/software/grep/manual/grep.html#index-_002do) |

## Basic Regular Expression (BRE) / Extended Regular Expression (ERE) Regular Expressions

> Example files: [`word_anchors.txt` and `words.txt`](https://github.com/learnbyexample/learn_gnugrep_ripgrep/tree/master/example_files/bre_ere)

Typical commands:

| Options | Description                                                                                                                                          |                             Manual Reference                            |
|:-------:|------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------:|
|   `-G`  | can be used to specify explicitly that BRE is needed                                                                                                 | [Link](https://www.gnu.org/software/grep/manual/grep.html#index-_002dG) |
|   `-E`  | will enable Extended Regular Expression (ERE). In GNU `grep`, BRE and ERE only differ in how metacharacters are specified, no difference in features | [Link](https://www.gnu.org/software/grep/manual/grep.html#index-_002dE) |
|   `-F`  | will cause the search patterns to be treated literally                                                                                               | [Link](https://www.gnu.org/software/grep/manual/grep.html#index-_002dF) |
|   `-P`  | will enable Perl Compatible Regular Expression (PCRE) (if available)                                                                                 | [Link](https://www.gnu.org/software/grep/manual/grep.html#index-_002dP) |

### Line Anchors

- `^` — start of line
- `$` — end of line
