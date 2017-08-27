
<div id="value"></div>

# Value

Python values are data that we refer by names.

```python
a = 45
s = 'string'
```
In above, `45` and `string` are two values. `a = 45` creates an `int` object with value `45` and is then referred by the name `a` where `s = 'string'` creates an `str` object with value `string` and referred by the name `s`.

> Python values are stored in memory and can not be deleted

One does not need to manage memory for the values. Python automatically allocates and deallocates memories as necessary.

> Same immutable value is not allocated twice (in most of the Python implementations including the default CPython)

```python
a = 9
b = 9
print(a is b) # output: True
```
In above, `9` is stored only once and have only one memory address, thus `a` and `b` both refers to the same memory location.

`str` objects:

```python
s1 = 'string'
s2 = 'string'
print(s1 is s2) # output: True
```
> Mutable values are always created (allocated) anew

```python
lst1 = [1, 2]
lst2 = [1, 2]
print(lst1 is lst2) # output: False
```
In above, `lst1` and `lst2` refers to different memory locations (two pieces of the same value).

> Python values are deleted when nothing references them

When there is no name that refers to a value, the value is picked up by the Python garbage collector and deleted automatically.

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


<div id="immutable-values"></div>


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

<div id="mutable-values"></div>

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

<div id="variable-name-or-reference"></div>

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

> A variable or name can refer to anything

```python
x = 3               # x refers to an int
x = 3.4             # now x refers to a float
x = 'str'           # now x refers to a string
x = [1, 2]          # now x refers to a list
def x():            # now x refers to a function
    return True

class x(object):    # now x refers to a class
    pass
```

> Python names or variables have no type

Python is dynamically typed i.e a name or variable can refer to any type of value at any time. For example, *x* can refer to an int, a float, a list, an arbitrary user defined type or any type at all.

> Deleting a name or variable does not delete its value

```python
x = 2
del x
```
In above, `del x` deletes (undefines/unsets) the name *x* but it does not delete the value that was being referenced by *x*. If there is no name referencing the value `2` then the Python garbage collector will delete the value automatically.

<div id="object"></div>

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
The literal `I am a string` is a value, and when it is used in Python i.e written within quotes (e.g `'I am a string'`), it's an (`str`) object.

> In python, everything is an object.

All data types such as *bool*, *int*, *str*; all classes, modules and functions are objects and almost all objects have attributes and methods.


<div id="expression"></div>

# Expression

Expression is something that operates on values and can yield a result. For example, `2 + 3` is an expression which can add two numbers to produce the sum.

<div id="statement"></div>

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

<div id="assignment"></div>

# Assignment

> Assignment is an statement that assigns a name to the reference to an object.

```python
var = 'A sample string'
```
Here, the name *var* refers to the `str` object `'A sample string'`.

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

> Assignment to different values always updates the reference

```python
x = 7
y = x
x = x + 2
print(x) # output: 9
print(y) # output: 7
```
The reference *x* was updated to refer to a new value `x + 2`.

> Assignment does not change values in-place

```python
lst = [1, 2]
lst = lst + [3]
```
In above, `[3]` is not appended to `lst` like it seems to be, `lst` and  `[3]` is being concatenated to create a new list and the reference `lst` is updated to refer to the new list.

> Names assigned by the same **immutable** value (not name) can share the reference

```python
x = 2
y = 2
print(x is y) # output: True
s1 = 'string'
s2 = 'string'
print(s1 is s2) # output: True
```
In above, both *x* and *y* refer to the same object (same for *s1* and *s2*).

> Names assigned by the same **mutable** value (not name) always refer to different objects altogether

```python
lst1 = [1, 2]
lst2 = [1, 2]
print(lst1 is lst2) # output: False
```
In above, *lst1* and *lst2* refer to different objects.

> Different names assigned by another name always refer to the same value regardless if the value is mutable or immutable

```python
x = 2
y = x
lst1 = [1, 2]
lst2 = lst1
print(x)    # output: 2
print(y)    # output: 2
print(lst1) # output: [1, 2]
print(lst2) # output: [1, 2]
```

So far, we have seen assignment with only the assignment operator `=`.

> There are lots of ways of assignment aside from the assignment operator `=`

```python
# assigns the name x to each item from an iterable in a loop
for x in iterator

# assigns a class to the name x
class x(...):

# assigns a function to the name x
def x(...):

# assigns the value 12 to a function parameter
func(12) # function call

# assigns the value referred by myvar to a function parameter
# i.e it's creating an alias for myvar in function scope
func(myvar) #function call

# assigns an object to the name x
... as x

# assigns a module object to the name x
import x
```
Each of the above is an assignment.

<div id="code block"></div>

# Code block

A code block is a piece of code that the python interpreter executes as a unit. The following are examples of code blocks:

* A module
* A function body
* A class definition
* Each command in interactive Python interpreter
* A script file
* A script command (passed with `-c` option of the Python interpreter)
* String argument passed to the built-in `eval()` and `exec()`

<div id="function"></div>

# Function

Function is an isolated block of code that performs some operation. We generally move our repetitive codes that we execute frequently to a dedicated code block so that we can re-use the block whenever necessary.

> We use a special keyword `def` to define a function

```python
def function_name(arguments):
    function body
```

> Functions can change mutable values in-place

```python
def f(lst):
    lst.extend([3, 4])

x = [1, 2]
f(x)        # changing x in-place
print(x)    # output: [1, 2, 3, 4]
```

> Functions can take anything and return anything

Functions can take and return objects. Everything in Python is an object, thus functions can return anything and take anything as argument.

```python
class X(object):
    pass

def f(arg):
    print(arg)
    return arg

f(12)       # output: 12
f('string') # output: 'string'
f([1, 2])   # output: [1, 2]
f(f)        # output: <function f at 0x7f15e203a8c0>
f(X)        # output: <class '__main__.X'>
```
In python functions are first class objects.

<div id="argument-and-parameter"></div>

# Argument & Parameter

Arguments are values that are passed with a function while Parameters are names that are assigned to the references of those values.

```python
func(12, 13, 14)
```
In above, `12`, `13` and `14` are arguments.

```python
def func(a, b, c):
    return a + b - c
```
In above, `a`, `b` and `c` are parameters.

<div id="scope"></div>

# Scope

The scope for a variable or name is the region where it is accessible or visible.

> Values don't have any scope, only names have scopes

A value can be referenced by a global or local variable alike, thus the term 'scope' does not make any sense for values. Only names can be global or local. This is the reason you can modify a value from anywhere.

> Changing a global name to reference to some other value is not permitted but the value itself can be changed.

```python
lst = [1, 2, 3, ] # A new list

def f():
    # you can not do the following:
    # Changing a global name to reference to some other value is not permitted
    # lst = lst + [4, 5]
    
    # but you can do the following:
    # to change the value itself
    lst.extend([4, 5])

f() # calling f()

print(lst)
```

> Global names are accessible to local scope

```python
x = 4
def f1():
    if x == 4:
        return x + 2 # returning the global x + 2
    else:
        return 0

f1() # output: 6
```

> Global names are not treated as global in local assignment

```python
x = 4
def f2():
    x = x + 3 # UnboundLocalError: local variable 'x' referenced before assignment
    return x

f2() # UnboundLocalError: local variable 'x' referenced before assignment
```
In above, when used in assignment, *x* is being treated as a local name not global.

> Global names become local in local assignment

```python
x = 4
def f():
    x = 3 # This x is no longer a global name
    return x # returning the local x

f() # output: 3
```
In above, when we change the *x* inside the function to refer to another value, it only does that in the local scope, the global *x* remains unmodified and untouched.

> Mutable values can be changed in-place using global names in local scope

```python
x = [1, 2]
def f():
    x.append(3)

f()
print(x) # output: [1, 2, 3]
```
The global name *x* can not be re-assigned but the value it refers to, can be changed in-place if mutable.

> Global names become both accessible and modifiable if declared with the `global` keyword in local scope

```python
x = 4
def f2():
    global x
    x = x + 3 # This is being treated as global
    return x

f2() # output: 7
```
In above, when we change the *x* inside the function to refer to another value, the global *x* is changed i.e *x* inside `f2()` is totally global now.

<div id="indentation"></div>

# Indentation

We separate blocks of python code by indentation. Consider the following example:

```python
if a is True:
    # inside if
    b = c + d
print(b) # outside if
```

Notice that there is no opening or closing bracket, there's an `if` but no `endif` or anything that appears to close this `if`. So how does this work actually?

Now, notice that the block of code inside `if` statement is indented with a certain amount of whitespaces. This little indentation tells python that the indented block belongs to the `if` statement.

> * It is necessary to have the same indentation with the same amount of whitespaces.
> * Tab is not equal to space, you can not put 4 spaces in a line and then a tab in the next and expect it to work correctly.
> * Use either tab or space not both.
> * The colon (`:`) after the end of the `if` conditional is mandatory.

Some more examples:

```python
if a is True:
    #inside first if
    if b is True:
        #inside second if
        if c is True:
            #inside third if
            print("Working with nested if")
        #inside second if but outside third if
    #inside first if but outside second if
#outside all ifs

for i in xrange(1,10):
    print(i)
    # inside for loop
# outside for loop

while i <= 9:
    print(i)
    #inside while loop
#outside while loop
```

> Indentation **does not** create a new scope.

In languages like C++, `if` statements, `for` loop, `while` loop create new scopes in their body, but in python they do not. Consider the following example:

```python
x = 0
for i in xrange(1,10):
    print(i)
    x = i + 1
print(x)
```

You are probably expecting the second `print` function to print `0`, but it won't, rather it will print `10`. Now that's strange right?

Well, in python, indentation does not create new scopes like the `{}` does in C++:

```cpp
{
    //This code is inside a new scope
    std::vector<int> a; //a is constructed here
} //a is destroyed here
a.push_back(32); //error, a is not declared in this scope.
```

Now in python, see these magics:

```python
for i in xrange(1,10):
    print(i)
    x = i + 1
print(x) # It's OK!! no error at all

if True:
    x = 5
else:
    y = 5
print(x) # OK
print(y) # NOT OK: NameError: name 'y' is not defined
```

Why did `print(y)` gave error? Spooky huh? Well, don't be afraid, no paranormal activities are in work here.

This is how it works:

1. python enters into `if True`
2. defines the name x with value 5
3. exits the `if`
4. does not enter into `else`, thus the `y = 5` never gets executed and thus `y` never gets defined.
5. print x
6. can not print y because it didn't reach the point where it could be defined.

