Regex to detect methods in javascript code, including ones with computed names (the computed names is the hard part).

```regex
^([a-zA-Z_$][\w$]*|\[(?:[^\]'"`]|(['"`])(?:\\.|(?!\2)[^\\])*\2)*\])\s*\(
```

Link: https://regex101.com/r/IIBcVk/3  
Explanation/detail link: https://regex101.com/r/8YvGK5/4

| Groups | Meaning |
| ------ | ------- |
| Entire match | The method name and the starting `(` of the parameters |
| Group 1 | The method name (if computed name, includes the `[]` around it) |
| Group 2 | ⚠️ Implementation detail: possibly stores the type of string currently being 'traversed' in the computed name |

Limitations:
- Doesn't fully handle syntax within the computed names (breaks down with nested brackets like `[[]](...args) { ... }` - i.e. using an empty array as the name)
