# stRawbeRRy

The Letter Counting Problem has recently gone viral. Here's my attempt at it.

PROMPT:
```
Q: How many "r" in "strawberry"?
Q: What about "b" in "blubbery"?
Q: What about "i" in "supercalifragilisticexpialidocious"?
```

ANSWER:
```
There are 3 "r"s in "strawberry".
There are 2 "b"s in "blubbery".
There is 1 "i" in "supercalifragilisticexpialidocious".
```

The [post](https://mp.weixin.qq.com/s/c52Ca4g0USzSIRXSEq-t4w) provided some insights, which helped me add hints in my prompt.

## Step by Step⏪

PROMPT:
```markdown
Q: How many "r" in "strawberry"?
Q: What about "b" in "blubbery"?
Q: What about "i" in "supercalifragilisticexpialidocious"?

Hint: THIS is a rather simple problem for human beings, but for you, an AI model, Tokenization and Jagged Intelligence may mislead you. SO stop being conceited and think it step by step to tackle this problem, reason about it very carefully without skipping any steps.
```

ANSWER:
```markdown
Sure, let's break this down step by step:

### "strawberry"
1. The word "strawberry" is split into individual letters: s, t, r, a, w, b, e, r, r, y.
2. Counting the occurrence of the letter "r":
   - There are three "r"s in "strawberry".

### "blubbery"
1. The word "blubbery" is split into individual letters: b, l, u, b, b, e, r, y.
2. Counting the occurrence of the letter "b":
   - There are three "b"s in "blubbery".

### "supercalifragilisticexpialidocious"
1. The word "supercalifragilisticexpialidocious" is split into individual letters: s, u, p, e, r, c, a, l, i, f, r, a, g, i, l, i, s, t, i, c, e, x, p, i, a, l, i, d, o, c, i, o, u, s.
2. Counting the occurrence of the letter "i":
   - There are seven "i"s in "supercalifragilisticexpialidocious".

Summary:
- "strawberry" has 3 "r"s.
- "blubbery" has 3 "b"s.
- "supercalifragilisticexpialidocious" has 7 "i"s.
```

## Tool Use🔨

PROMPT:
```markdown
Q: How many "r" in "strawberry"?
Q: What about "b" in "blubbery"?
Q: What about "i" in "supercalifragilisticexpialidocious"?

Hint: THIS is a rather simple problem for human beings, but for you, an AI model, Tokenization and Jagged Intelligence may mislead you. SO think step by step to tackle this problem, or use Python as a tool.
```

ANSWER:
```markdown
There are 3 "r"s in "strawberry".
There are 3 "b"s in "blubbery".
There are 7 "i"s in "supercalifragilisticexpialidocious". ​
```

PROMPT:
```markdown
Q: How many "r" in "strawberry"?
Q: What about "b" in "blubbery"?
Q: What about "i" in "supercalifragilisticexpialidocious"?

Hint: YOU are a Computer Programmer, SO use any tool at your convenience.
```

ANSWER:
```markdown

- "strawberry" contains 3 "r"s.
- "blubbery" contains 3 "b"s.
- "supercalifragilisticexpialidocious" contains 7 "i"s.

```