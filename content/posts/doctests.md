---
title: "doctests"
date: 2022-02-28T18:48:23-08:00
draft: false
tags: ["python", "programming", "testing", "doctest", "interviews"]
---

Consider some small utility function such as:
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

These utility functions typically have a small footprint, and they are usually
tested by writing unittests for functions that call these small utility 
functions/method. Testing them directly within the test suite can be done, but
if you start adding multiple files for multiple utility functions keeping track
of the changes can become a chore.

Enter [doctest](https://docs.python.org/3/library/doctest.html), this module 
enables tests be embedded into docstrings. It's great! As the code is changed, 
the tests can be updated to ensure that the utility works as expected, and the 
number of test files is reduced.

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
interview much ha!). When your interviewer is dropping the prompt into the 
shared code environment (CodePen), take the examples that they provide and 
create doctests with them. It shows some level of interest within how the 
codebase is groomed, and you get to flex the tests while working on the code.

During the preliminary interview process you might be able to probe to find out
what whiteboarding tools the company uses. One such application is 
[CoderPad](https://app.coderpad.io/sandbox), checkout the sandbox to test what 
works. Paste the example with the docstring into the editor, in the console run:
```python
# From the active python console
>>>  import doctest; doctest.testmod(name='parse_string', verbose=True)
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
