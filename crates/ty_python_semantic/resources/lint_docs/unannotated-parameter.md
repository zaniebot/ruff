## What it does

Checks for function parameters without an annotation. The first positional parameter of an instance
method or class method is exempt because ty infers its type from the class.

## Why is this bad?

An unannotated parameter accepts values of any type. A default value tells ty what happens when the
argument is omitted, but does not constrain the arguments callers can pass.

## Examples

```python
def double(value=0):  # error: [unannotated-parameter]
    return value * 2
```

With an annotation, ty can check callers against the intended parameter type.

```python
def double(value: int = 0):
    return value * 2
```
