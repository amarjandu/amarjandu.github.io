---
title: "doctests"
date: 2022-02-28T18:48:23-08:00
draft: false
tags: ["python", "programming", "testing", "doctest", "interviews"]
---

Consider some small function such as:
```python
def parse_string(input: str):
    try:
        name, value = input.split(':')
    except ValueError:
        name  = input
        value = None
    assert name, input
    return name, value
```

These utility functions typically have a small footprint, yet there can be 
dozens of them scattered in a codebase. Testing them directly within the 
test suite can be done, but if you start adding multiple files for multiple 
utility functions, the disassociation between proximity of definition and 
location of tests make it annoying to maintain.

Enter [doctest](https://docs.python.org/3/library/doctest.html), this module 
enables tests be embedded into docstrings. The proximity to the code definition
makes it really easy to maintain the tests, it's great!

For the example above:

```python
def parse_string(input: str):
    """
    >>> parse_string('foo:bar')
    ('foo', 'bar')

    >>> parse_string('baz')
    ('baz', None)

    >>> parse_string(':foo')
    Traceback (most recent call last):
    ...
    AssertionError: :foo
    """
    try:
        name, value = input.split(':')
    except ValueError:
        name  = input
        value = None
    assert name, input
    return name, value
```

This kind of testing also can help with an interview process, typically 
interviewers are looking for developers to mention testing the code that they 
write (it's probably one of those checkbox item things don't ask me I dont 
interview much ha!). When your interviewer is sharing the exercise into the 
whiteboarding environment (CodePen), take the examples that they provide and 
create doctests with them. Explain the choice of creating tests in proximity of 
the definition, and why it's useful.

During the preliminary interview process you might be able to probe to find out
what whiteboarding tools the company uses. One such application is 
[CoderPad](https://app.coderpad.io/sandbox), checkout the sandbox to test what 
works.

In CoderPad you can paste this at the end of the editor, and it should perform 
the doctests every time you save the file. Alternatively you can paste the code 
into the python console (annoying UX have to keep copy and pasting).
```python
# Make sure to copy the function `parse_string` from above
>>>  import doctest; doctest.testmod(name='parse_string', verbose=True)

Guest ran 22 lines of Python 3 (finished in 1.14s):

Trying:
    parse_string('foo:bar')
Expecting:
    ('foo', 'bar')
ok
Trying:
    parse_string('baz')
Expecting:
    ('baz', None)
ok
Trying:
    parse_string(':foo')
Expecting:
    Traceback (most recent call last):
    ...
    AssertionError: :foo
ok
1 items had no tests:
    parse_string
1 items passed all tests:
   3 tests in parse_string.parse_string
3 tests in 2 items.
3 passed and 0 failed.
Test passed.
TestResults(failed=0, attempted=3)
```

You get to test the code that you are whiteboarding, and you can flex your
knowledge about doctests. :)
