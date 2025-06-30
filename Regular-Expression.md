# Regular-Expression
I had learned Python before, but I didn’t realize how important regular expressions are.  
If you are going to clean data or do something repetitive and mechanical with data,regular expressions should be your first choice.　　
In case you are Japanese there are Japanese website.
[正規表現（Regular Expressions）文法解説 - Qiita](https://qiita.com/luohao0404/items/7135b2b96f9b0b196bf3)
# Grammar
| Pattern     | Meaning                             | Example |
|-------------|-------------------------------------|---------|
| `.`         | Any character except newline        | `a.c` matches `abc`, `a1c`, `a-c` |
| `^`         | Start of string                     | `^Hello` matches `Hello world`, but not `Say Hello` |
| `$`         | End of string                       | `world$` matches `Hello world` |
| `*`         | 0 or more repetitions               | `lo*l` matches `ll`, `lol`, `lool` |
| `+`         | 1 or more repetitions               | `lo+l` matches `lol`, `lool` but not `ll` |
| `?`         | 0 or 1 repetition                   | `colou?r` matches `color` and `colour` |
| `\d`        | Digit (0–9)                         | `\d+` matches `2025`, `123` |
| `\w`        | Word character                      | `\w+` matches `hello123` |
| `\s`        | Whitespace                          | `\s+` matches space, tab, etc. |
| `{n}`       | Exactly n repetitions               | `\d{4}` matches `2025` |
| `{n,}`      | n or more repetitions               | `\d{2,}` matches `23`, `45678`, etc.|
| `{n,m}`     | Between n and m repetitions         | `\d{2,4}` matches `12`, `123`, `1234` |
| `[abc]`     | One character: a, b, or c           | `[aeiou]` matches any vowel |
| `[^abc]`    | Any character except a, b, or c     | `[^0-9]` matches any non-digit |
| `( ... )`   | Capturing group                     | `(\d+)-(\d+)` matches `123-456` and captures `123`, `456` |
| `|`         | OR                                  | `cat|dog` matches either `cat` or `dog` |

## Special Instructions
### different between * and +
```Python
import re

test_cases = ["aaa", "aaab", "b", ""]

pattern_star = r"a*"
pattern_plus = r"a+"

print("Testing a*")
for s in test_cases:
    result = re.findall(pattern_star, s)
    print(f"Input: '{s}' => Matches: {result}")

print("\nTesting a+")
for s in test_cases:
    result = re.findall(pattern_plus, s)
    print(f"Input: '{s}' => Matches: {result}")
```
**result**  
Testing a*  
Input: 'aaa'  => Matches: ['aaa', '']　&nbsp;　# 2 results: 'aaa' + '' (empty match at the end)  
Input: 'aaab' => Matches: ['aaa', '', '']　&nbsp;　# Matches 'aaa', then empty matches after 'b' and at the end  
Input: 'b'    => Matches: ['', '']　&nbsp;　# No 'a', but empty matches at position 0 and at the end  
Input: ''     => Matches: ['']　&nbsp;　# Empty string matches once  

Testing a+  
Input: 'aaa'  => Matches: ['aaa']　&nbsp;　# Matches one or more 'a's once  
Input: 'aaab' => Matches: ['aaa']　&nbsp;　# Matches 'aaa', no match on 'b'  
Input: 'b'    => Matches: []　&nbsp;　# No 'a' found, no matches  
Input: ''     => Matches: []　&nbsp;　# Empty string, no matches  

### 
