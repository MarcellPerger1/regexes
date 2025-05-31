Regex to detect all classes in a file, useful to auto-generate `__all__` for a large file.

```regex
^(?:(?!class|').*\n)*^class\s+(\w+)[^\n]+:(?:[ \t]*#[^\n]+)?(?=$)(?:\n(?!class|')[^\n]*)*
```

If using it to generate `__all__`, set the substitution to `'$1',`, then put `[]` around the result. Note that it doesn't generate entries for functions and constants.

Link: https://regex101.com/r/Bms5Vx/2

Limitations:
- This is a very dumb regex. Multiple-line string literals containing a line starting with the word `class` might break it.
