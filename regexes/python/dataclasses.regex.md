A regex to detect dataclasses:
```regex
@dataclass(\([^)\n]*\))?[ \t]*(?:#[^\n]*)?\nclass\s+(\w+)(\([^)\n]*\))?:(?:[ \t]*#[^\n]*)?\n(?:\s+"""[^"]+""")?(?:\s*(?:#[^\n]*)?\n)*(?=([\t ]+))(?:\4[^\n]+\n|\n)*
```
Link: https://regex101.com/r/XmABXa/3

| Group | Meaning |
| ----- | ------- |
| Match | The entire dataclass, including the body |
| Group 1 | The dataclass decorator arguments |
| Group 2 | The name |
| Group 3 | The base classes (if any) |
