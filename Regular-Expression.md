# Regular-Expression
I had learned Python before, but I didn’t realize how important regular expressions are.  
If you are going to clean data or do something repetitive and mechanical with data,regular expressions should be your first choice.

# Grammar
| Pattern     | Meaning                             | Example |
|-------------|-------------------------------------|---------|
| `.`         | Any character except newline        | `a.c` matches `abc`, `a1c`, `a-c` |
| `^`         | Start of string                     | `^Hello` matches `Hello world`, but not `Say Hello` |
| `$`         | End of string                       | `world$` matches `Hello world` |
| `*`         | 0 or more repetitions               | `lo*l` matches `ll`, `lol`, `lool` |
| `+`         | 1 or more repetitions               | `lo+l` matches `lol`, `lool` but not `ll` |
| `?`         | 0 or 1 repetition                   | `colou?r` matches `color` and `colour` |
| `{n}`       | Exactly n repetitions               | `\d{4}` matches `2025` |
| `{n,}`      | n or more repetitions               | `\d{2,}` matches `23`, `45678`, etc. |
| `{n,m}`     | Between n and m repetitions         | `\d{2,4}` matches `12`, `123`, `1234` |
| `\d`        | Digit (0–9)                         | `\d+` matches `2025`, `123` |
| `\w`        | Word character                      | `\w+` matches `hello123` |
| `\s`        | Whitespace                          | `\s+` matches space, tab, etc. |
| `[abc]`     | One character: a, b, or c           | `[aeiou]` matches any vowel |
| `[^abc]`    | Any character except a, b, or c     | `[^0-9]` matches any non-digit |
| `( ... )`   | Capturing group                     | `(\d+)-(\d+)` matches `123-456` and captures `123`, `456` |
| `|`         | OR                                  | `cat|dog` matches either `cat` or `dog` |
