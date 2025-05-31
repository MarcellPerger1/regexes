A regex to detect dataclasses:
```regex
@dataclass(\([^)\n]*\))?[ \t]*(?:#[^\n]*)?\nclass\s+(\w+)(\([^)\n]*\))?:(?:[ \t]*#[^\n]*)?\n(?:\s+"""[^"]+""")?(?:\s*(?:#[^\n]*)?\n)*(?=([\t ]+))(?:\4[^\n]+\n|\n)*
```
Link: https://regex101.com/r/XmABXa/3.

| Group | Meaning |
| ----- | ------- |
| Match | The entire dataclass, including the class body |
| Group 1 | The dataclass decorator arguments (if any) |
| Group 2 | The class name |
| Group 3 | The base classes (if any) |

Limitations:
- Doesn't work if there's another decorator on the class
