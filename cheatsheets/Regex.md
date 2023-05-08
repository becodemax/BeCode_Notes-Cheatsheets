### What's that?

Regex (short for regular expression) is a sequence of characters that define a search pattern. In Python, regex is implemented as a module named `re`. It allows you to search and manipulate strings based on patterns.

Regex patterns can include a combination of regular characters (such as letters and digits) and special characters (such as `.` and `*`) that have a special meaning within a regex pattern. These special characters are used to define the search pattern in a more flexible way than just searching for exact matches of specific strings.

The `re` module in Python provides a set of functions that allow you to use regular expressions to search for patterns within strings, split strings based on patterns, replace substrings based on patterns, and more. The most commonly used functions in the `re` module are `re.match()`, `re.search()`, `re.findall()`, `re.sub()`, and `re.split()`.

Here's a brief explanation of each of these functions:

-   `re.search(pattern, string)` - searches for the first occurrence of the pattern in the string and returns a match object if found.
-   `re.match(pattern, string)` - checks if the pattern matches at the beginning of the string and returns a match object if found.
-   `re.findall(pattern, string)` - searches for all occurrences of the pattern in the string and returns a list of all matching substrings.
-   `re.sub(pattern, replacement, string)` - replaces all occurrences of the pattern in the string with the replacement string.

### Syntax and patterns

-   `a|b`– Match either “a” or “b
-   `?` – Zero or one
-   `+` – one or more
-   `*` – zero or more
-   `{N}` – Exactly N number of times (where N is a number)
-    `{N,}` – N or more number of times (where N is a number)
-   `{N,M}` – Between N and M number of times (where N and M are numbers and N < M)
-   `*?` – Zero or more, but stop after first match
- -   `[A-Z]`– Match any uppercase character from “A” to “Z”
-   `[a-z]`– Match any lowercase character from “a” to “z”
-   `[0-9]` – Match any number
-   `[asdf]`– Match any character that’s either “a”, “s”, “d”, or “f”
-   `[^asdf]`– Match any character that’s not any of the following: “a”, “s”, “d”, or “f”
- -   `.` – Any character
-   `\n` – Newline character
-   `\t` – Tab character
-   `\s`– Any whitespace character (including `\t`, `\n` and a few others)
-   `\S` – Any non-whitespace character
-   `\w`– Any word character (Uppercase and lowercase Latin alphabet, numbers 0-9, and `_`)
-   `\W`– Any non-word character (the inverse of the `\w` token)
-   `\b`– Word boundary: The boundaries between `\w` and `\W`, but matches in-between characters
-   `\B`– Non-word boundary: The inverse of `\b`
-   `^` – The start of a line
-   `$` – The end of a line 
-   `\`– The literal character “\”

### Examples :

find positive/negative digitals :
```
re.findall(r'-?\d+', string)
```

find all digits :
```
re.findall(r'\d', string)
```

find any words ending by "ly" :
```
re.findall(r'\w+ly', string)
```

license plate pattern :
```
pattern = r'^[A-Z]{2}-[0-9]{3}-[A-Z]{2}$'
```

ipv4 address pattern :
```
pattern = r'^(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?).(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?).(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?).(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)$'
```

mail pattern :
```
mail_pattern = r'^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$'
```

password longer than 6 chars pattern :
```
password_pattern = r'.{6,}'
```
