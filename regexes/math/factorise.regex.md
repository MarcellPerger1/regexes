A regex that factorises a number (gives one of its factors). The number is expressed as a sequence of `x`s, with the length of the seqeuence being the number to be expressed (e.g. 6 -> `xxxxxx`)

```regex
^(x{2,})\1+$
```

Link: https://regex101.com/r/YFjNu8/1

| Group | Meaning |
| ----- | ------- |
| Full Match | Mathes the entire string if it can be factorised. If it is a prime number (or 1), it doesn't match anything |
| Group 1 | One of its factors (generally the largest one) |

Limitations:
- For large hard-to-factorise numbers, it starts to experience [catastrophic backtracking](https://www.regular-expressions.info/catastrophic.html) and fails (11733 seems to be the first one that gives this error).
- DO NOT use this in actual code to check if a number is prime! This is simply here as a 'wow, you can do that with regex?!'
