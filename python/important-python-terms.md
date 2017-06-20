
# Value

Python values are data that we refer by names.

```python
a = 45
s = 'string'
```
In above, `45` and `string` are two values. `a = 45` creates an `int` object with value `45` and is then referred by the name `a` where `s = 'string'` creates an `str` object with value `string` and referred by the name `s`.

One does not need to manage memory for the values. Python automatically allocates and deallocates memories as necessary.

> Same immutable value is not allocated twice within a scope (in most of the Python implementations including the default CPython)

```python
a = 9
b = 9
a is b # output: True
```
In above, `9` is stored only once and have only one memory address, thus `a` and `b` both refers to the same memory location.

`str` objects:

```python
s1 = 'string'
s2 = 'string'
s1 is s2 # output: True
```
> Mutable values are always created (allocated) anew

```python
lst1 = [1, 2]
lst2 = [1, 2]
lst1 is lst2 # output: False
```
In above, `lst1` and `lst2` refers to different memory locations (two pieces of the same value).


> Changes in a value will be common to all of its names

```python
lst1 = [1, 2]
# let lst2 refer to the same list as lst1
lst2 = lst1
lst1.append(3)
print(lst2) # output: [1, 2, 3]
```
In above, we changed the value `[1, 2]` (in place) using the reference `lst1` and it was visible through `lst2`. This is aliasing and we can say that `lst2` is just an alias of `lst1`.

> Changes in a value will **not** be common to all of its names if the changes are not done in-place

If we did not change the value in place and created a new value instead, `lst2` would no longer be an alias of `lst1`:

```python
lst1 = [1, 2]
# let lst2 refer to the same list as lst1
lst2 = lst1
lst1 = lst1 + [3]
print(lst2) # output: [1, 2]
```
`lst1 + [3]` creates a new list by adding an elemnt `3` at the end of `lst1` and assigns the result to `lst1`, thus `lst1` no longer refers to the same value. `lst2` still retains the reference to the value that was referred by `lst1` previously.

## Immutable values

Values that can not be changed in-place are called immutable. Changing an immutable value always creates a new value:

```python
x = 6
y = x
x = x + 1
print(x) # output: 7
print(y) # output: 6
```
In above, `x + 1` creates a new value (`7`) and a reference to this new value is assigned to `x` while `y` still retains the reference to the previous value.

## Mutable values

Values that can be changed in-place are mutable.

```python
lst1 = [1, 2]
lst2 = lst1
lst1.append(3)
print(lst1) # output: [1, 2, 3]
print(lst2) # output: [1, 2, 3]
```
Here, the `append()` method changes the list in-place, thus no new list is being created.


# Variable, Name or Reference

Python variables are different from variables in other programming languages like C++, Java etc.

A python *variable* (or *name*) is just a reference to a value. A variable does not store the value, rather it is just a reference to the memory location where the value is stored.

> Multiple names can refer to a single value.

```python
a = 5
b = 5
```
In above, `5` is a vlue that is stored in the memory (only once not twice) and both `a` and `b` refer to it.

> A variable or name **never** refers to another variable or name

```python
a = 5
b = a
```
In above, `b` is a reference to `5` not to `a`. If you change the value of `a` (`a = 6` or whatever), `b` will still refer to `5`.



# Object

In python, everything that can be assigned to a variable or passed as an argument to a function is an object. Thus values themselves are objects, e.g `5` is an `int` object, `'I am a string'` is an `str` object etc.

> All values can be objects but not all objects can be values

```python
import sys
print(sys.path)
```
In above, `sys` is an object but it's not a value.

```python
s = 'I am a string'
```
The literal `I am a string` is a value, and when it is written within quotes (e.g `'I am a string'`), it's an (`str`) object.

All data types such as *bool*, *int*, *str*; all classes, modules and functions are objects and almost all objects have attributes and methods.

> In python, everything is an object.



# Expression

Expression is something that operates on values and can yield a result. For example, `2 + 3` is an expression which can add two numbers to produce the sum.



# Statement

Statement is a block of code that the python interpreter executes to do some task. The simplest example is the assignment statement:

```python
a = 15
```
The above is an statement that the python interpreter executes to create an `int` object with value `15` and assigns it to the name `a`.

Expressions themselves are statements (`2 + 3` is executed by the python interpreter, thus it's an statement)

> All expressions are statements but all statements are not expressions

`a = 15` is not an expression (it does not operate on anything).

```python
a = 2 * 3
```
In above, `a = 2 * 3` is not an expression but an statement while `2 * 3` is an expression.



# Assignment

Assignment is an statement that assigns a name to the reference to a value or object.

```python
var = 'A sample string'
```
Here, the name *var* refers to the value `A sample string`.

> Assignment never copies data

If you come from a C++ background, you will find out that Python assignment can be very different compared to C++ assignment.

While C++ assignment performs copy:

```cpp
object1 = object2
//object1 gets a copy of object2
//whether the copy is a shallow one or a deep one
//is defined by the corresponding class'es copy constructor
```
Python assignment makes a new reference/name without any copy:

```python
object1 = object2
# object1 refers the same thing as object2
```


# Function

Function is an isolated block of code that performs some operation.

