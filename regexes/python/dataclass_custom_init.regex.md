Regex to detect all dataclasses with a custom `__init__` method. Can be modified to be any other method as custom.

```regex
@dataclass(\([^)\n]*\))?[ \t]*(?:#[^\n]*)?\nclass\s+(\w+)(\([^)\n]*\))?:(?:[ \t]*#[^\n]*)?\n(?:\s+"""[^"]+""")?(?:\s*(?:#[^\n]*)?\n)*(?=([\t ]+))(?:\4(?!def[ \t]+__init__)[^\n]+\n|\n)*(?:\4(def[ \t]+__init__\([^\n]*)\n)(?:\4(?!def[ \t]+__init__)[^\n]+\n|\n)*
```

To change it to detect any other method as 'custom/overridden', change all 3 `__init__`s to the method you want to detect (these are located towards the end of the regex).


| Group | Meaning |
| ----- | ------- |
| Match | The entire dataclass, including the class body |
| Group 1 | The dataclass decorator arguments (if any) |
| Group 2 | The class name |
| Group 3 | The base classes (if any) |
| Group 4 | ⚠️ (Implementation details, do not use) The indenetation for the class |
| Group 5 | Location of the method (the method declaration, first line only) |

Link: https://regex101.com/r/NinkyW/1

Limitations:
- Doesn't work if there's another decorator between the `@dataclass` and the `class Whatever: ...`
