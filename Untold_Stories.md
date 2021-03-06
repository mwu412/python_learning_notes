# Untold Stories of Python
Micheal Wu

## Can I change the data itself? How?

#### Modify the df of Pandas:

`df.drop('label')` will do nothing to `df`

We should:

`df = df.drop('label')` 

trivial but tricky right?

#### What about Numpy array?

[Numpy arrays are immutable](https://docs.scipy.org/doc/numpy/reference/arrays.scalars.html).

Therefore, we must assign it to a new one:

`new_arr = np.delete(arr, [1, 3, 5])`

#### What about Python list?

Python lists are mutable.

The one line `list_a.extend([1, 2, 3])` will modify the python list `list_a`)

## Python List: append() v.s. extend()
https://stackoverflow.com/questions/252703/difference-between-append-vs-extend-list-methods-in-python

`list_a.extend([0])` will work

`list_a.extend(0)` will fail

## Global Variable?
```python
status = True

def main():
  if a:
    status = False
  if status:
    pass
```
Will return error: *local variable 'status' referenced before assignment*

Note that `main()` is a function.

From [ref](https://stackoverflow.com/questions/17506947/local-variable-referenced-before-assignment-in-python) and 
[docs](https://docs.python.org/release/1.5.1p1/tut/functions.html):

> All variabale assignments in a function store the value in the local symbol table; whereas variable references first look in the local symbol table, then in the global symbol table, and then in the table of built-in names. Thus, global variables cannot be directly assigned a value within a function (unless named in a global statement), although they may be referenced.

If a variable is declared in the global scope but we want to access it in a local scope, we should add a line `global myvar` before accessing it.

## Loop Over Both Key and Value of a Dict

Loop over key: `for key in d:`

Loop over both: `for key, value in d.items():`

#### Dimension of numpy.array
```python
numpy.array([0, 0, 0])
```
This is a 4 elements one dimension array.
However,
```python
numpy.array([[0, 0, 0]])
```
or
```python
numpy.array([0, 0, 0], ndmin=2)
```
is a 1x4 two-dimensional array.
