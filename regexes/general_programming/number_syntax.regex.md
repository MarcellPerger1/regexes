Regex to match number literals

```regex
^([+-]?)(\d*\.\d+|\d+\.?)(?:[eE]([+-]?\d+))?
```

Link: https://regex101.com/r/2EogTA/1

| Group | Meaning |
| ----- | ------- |
| Entire match | The full number |
| Group 1 | The `+` or `-` sign, or empty |
| Group 2 | The main bit of the number |
| Group 3 | The exponent, including its sign (if present) |
