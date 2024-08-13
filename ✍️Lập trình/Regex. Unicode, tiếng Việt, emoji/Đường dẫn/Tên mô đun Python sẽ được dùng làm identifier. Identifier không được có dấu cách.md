---
share: true
created: 2023-10-30T14:29
updated: 2024-08-13T21:05
---

You should take the spaces out of the filename. Because the filename is used as the identifier for imported modules (i.e. `foo.py` will be imported as `foo`) and Python identifiers can't have spaces, this isn't supported by the `import` statement.

If you _really_ need to do this for some reason, you can use the `__import__` function:

```python
foo_bar = __import__("foo bar")
```

This will import `foo bar.py` as `foo_bar`. This behaves a little bit different than the `import` statement and you should avoid it.

Nguồn:: [How do you import a file in python with spaces in the name? (duplicate)](https://stackoverflow.com/a/9123555/3416774)