Format for the exercise is:

- use the [`dracula.txt`](dracula.txt) file as input
- output is shown for every question within code blocks
- answer is in code blocks

1. Display all lines containing `ablaze`:

    ```text
    the room, his face all ablaze with excitement. He rushed up to me and
    ```

    ```bash
    grep 'ablaze' dracula.txt
    ```

1. Display all lines containing `abandon` as a whole word:

    ```text
    inheritors, being remote, would not be likely to abandon their just
    ```

    ```bash
    grep -w 'abandon' dracula.txt
    ```

1. Display all lines that satisfies both of these conditions:

    - `professor` matched irrespective of case
    - either `quip` or `sleep` matched case sensitively

    ```text
    equipment of a professor of the healing craft. When we were shown in,
    its potency; and she fell into a deep sleep. When the Professor was
    sleeping, and the Professor seemingly had not moved from his seat at her
    to sleep, and something weaker when she woke from it. The Professor and
    ```

    ```bash
    grep -i 'professor' dracula.txt | grep -e 'quip' -e 'sleep'
    ```

1. Display first three lines containing `Count`:

    ```text
    town named by Count Dracula, is a fairly well-known place. I shall enter
    must ask the Count all about them.)
    Count Dracula had directed me to go to the Golden Krone Hotel, which I
    ```

    ```bash
    grep -m3 'Count' dracula.txt
    ```

1. Display first six lines containing `Harker` but not either of `Journal` or `Letter`:

    ```text
    said, "The Herr Englishman?" "Yes," I said, "Jonathan Harker." She
    "I am Dracula; and I bid you welcome, Mr. Harker, to my house. Come in;
    I shall be all alone, and my friend Harker Jonathan--nay, pardon me, I
    Jonathan Harker will not be by my side to correct and aid me. He will be
    "I write by desire of Mr. Jonathan Harker, who is himself not strong
    junior partner of the important firm Hawkins & Harker; and so, as you
    ```

    ```bash
    grep -v -e 'Journal' -e 'Letter' dracula.txt | grep -m6 'Harker'
    ```

1. Display lines containing `Zooelogical Gardens` along with line number prefix:

    ```text
    5597: _Interview with the Keeper in the Zooelogical Gardens._
    5601:the keeper of the section of the Zooelogical Gardens in which the wolf
    8042:the Zooelogical Gardens a young one may have got loose, or one be bred
    ```

    ```bash
    grep -n 'Zooelogical Gardens' dracula.txt
    ```

1.  Find total count of whole word `the` (irrespective of case):

    ```text
    8090
    ```

    ```bash
    grep -iow 'the' dracula.txt | wc -l
    ```

1. The below code snippet tries to get number of empty lines, but apparently shows wrong result, why?

    ```bash
    $ grep -cx '' dracula.txt
    0
    ```

    `dracula.txt` is not a Unix-style file format:

    ```bash
    file dracula.txt
    
    dracula.txt: ASCII text, with CRLF line terminators
    ```

    This can be further reviewed using the `od` command ([manual](https://man7.org/linux/man-pages/man1/od.1.html)):

    ```bash
    od -c dracula.txt | head -n5

    0000000    T   h   e       P   r   o   j   e   c   t       G   u   t   e
    0000020    n   b   e   r   g       E   B   o   o   k       o   f       D
    0000040    r   a   c   u   l   a   ,       b   y       B   r   a   m    
    0000060    S   t   o   k   e   r  \r  \n  \r  \n   T   h   i   s       e
    0000100    B   o   o   k       i   s       f   o   r       t   h   e    
    ```

    This normally means there aren't any empty lines as there are (at least) a `\r` character in every other line other than the new line.

    In order to resolve this, add the `$'\r'` to the `grep` command:

    ```bash
    grep -cx $'\r' dracula.txt

    2559
    ```
