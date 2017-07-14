注意搜索Note可以得到比较重要的知识点

`*args `和  `**kwargs`

```python
# *args是可变的positional arguments（tuple），**kwargs是可变的keyword arguments（dict）。并且，在传递参数的时候，参数的放置位置要注意，参数是有顺序的，*args的参数必须位于**kwargs参数之前，因为positional arguments必须位于keyword arguments之前。
def foo(*args, **kwargs):
    print 'args = ', args
    print 'kwargs = ', kwargs
    print '---------------------------------------'

if __name__ == '__main__':
    foo(1,2,3,4)
    foo(a=1,b=2,c=3)
    foo(1,2,3,4, a=1,b=2,c=3)
    foo('a', 1, None, a=1, b='2', c=3)
输出结果如下：
args =  (1, 2, 3, 4) 
kwargs =  {} 
--------------------------------------- 
args =  () 
kwargs =  {'a': 1, 'c': 3, 'b': 2} 
--------------------------------------- 
args =  (1, 2, 3, 4) 
kwargs =  {'a': 1, 'c': 3, 'b': 2} 
--------------------------------------- 
args =  ('a', 1, None) 
kwargs =  {'a': 1, 'c': 3, 'b': '2'} 
---------------------------------------

可以看到，这两个是python中的可变参数。*args表示任何多个无名参数，它是一个tuple；**kwargs表示关键字参数，它是一个dict。并且同时使用*args和**kwargs时，必须*args参数列要在**kwargs前，像foo(a=1, b='2', c=3, a', 1, None, )这样调用的话，会提示语法错误“SyntaxError: non-keyword arg after keyword arg”。

呵呵，知道*args和**kwargs是什么了吧。还有一个很漂亮的用法，就是创建字典：

    def kw_dict(**kwargs):
        return kwargs
    print kw_dict(a=1,b=2,c=3) == {'a':1, 'b':2, 'c':3}
其实python中就带有dict类，使用dict(a=1,b=2,c=3)即可创建一个字典了。
```

```python
# python中`if __name__ == '__main__': `的解析

当你打开一个.py文件时,经常会在代码的最下面看到if __name__ == '__main__':
    模块是对象，并且所有的模块都有一个内置属性 __name__。一个模块的 __name__ 的值取决于您如何应用模块。如果 import 一个模块，那么模块__name__ 的值通常为模块文件名，不带路径或者文件扩展名。但是您也可以像一个标准的程序样直接运行模块，在这种情况下, __name__ 的值将是一个特别缺省"__main__"。

////////////////////////////////////////////

在cmd 中直接运行.py文件,则__name__的值是'__main__';

而在import 一个.py文件后,__name__的值就不是'__main__'了;

从而用if __name__ == '__main__'来判断是否是在直接运行该.py文件

如:
#Test.py

class Test:
    def __init(self):pass
    def f(self):print 'Hello, World!'
if __name__ == '__main__':
    Test().f()
#End

你在cmd中输入:
C:>python Test.py
Hello, World!
说明:"__name__ == '__main__'"是成立的

你再在cmd中输入:
C:>python
>>>import Test
>>>Test.__name__                #Test模块的__name__
'Test'
>>>__name__                       #当前程序的__name__
'__main__'

无论怎样,Test.py中的"__name__ == '__main__'"都不会成立的!
所以,下一行代码永远不会运行到!
```

Python was created by Guido Van Rossum in the early 90s. It is now one of the most popular languages in existence. I fell in love with Python for its **syntactic clarity**. ==It's basically executable pseudocode.基于可执行的伪代码。==

**Note**: This article applies to Python 2.7 specifically, but should be applicable to Python 2.x. Python 2.7 is reaching end of life and will stop being maintained in 2020, it is though recommended to start learning Python with
Python 3. For Python 3.x, take a look at the [Python 3 tutorial](http://learnxinyminutes.com/docs/python3/).

==It is also possible to write Python code which is compatible with Python 2.7 and 3.x at the same time, using Python [`__future__` imports](https://docs.python.org/2/library/__future__.html). `__future__` import sallow you to write Python 3 code that will run on Python 2, so check out the Python 3 tutorial.==

```python

# Single line comments start with a number symbol.

""" Multiline strings can be written
    using three "s, and are often used
    as comments
"""

####################################################
# 1. Primitive Datatypes and Operators
####################################################

# You have numbers
3  # => 3

# Math is what you would expect
1 + 1  # => 2
8 - 1  # => 7
10 * 2  # => 20
35 / 5  # => 7

# Division is a bit tricky. It is integer division and floors the results
# automatically.
5 / 2  # => 2

# To fix division we need to learn about floats.
2.0  # This is a float
11.0 / 4.0  # => 2.75 ahhh...much better

# Result of integer division truncated down both for positive and negative.
5 // 3  # => 1
5.0 // 3.0  # => 1.0 # works on floats too
-5 // 3  # => -2
-5.0 // 3.0  # => -2.0

！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！
# Note that we can also import division module(Section 6 Modules)
# to carry out normal division with just one '/'.
from __future__ import division
！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！

11 / 4  # => 2.75  ...normal division
11 // 4  # => 2 ...floored division

# Modulo operation
7 % 3  # => 1

# Exponentiation (x to the yth power)
2 ** 4  # => 16

# Enforce precedence with parentheses
(1 + 3) * 2  # => 8

# Boolean Operators
# Note "and" and "or" are case-sensitive
True and False  # => False
False or True  # => True

# Note using Bool operators with ints
0 and 2  # => 0
-5 or 0  # => -5
0 == False  # => True
2 == True  # => False
1 == True  # => True

# negate with not
not True  # => False
not False  # => True

# Equality is ==
1 == 1  # => True
2 == 1  # => False

# Inequality is !=
1 != 1  # => False
2 != 1  # => True

# More comparisons
1 < 10  # => True
1 > 10  # => False
2 <= 2  # => True
2 >= 2  # => True

# Comparisons can be chained!
1 < 2 < 3  # => True
2 < 3 < 2  # => False

# Strings are created with " or '
"This is a string."
'This is also a string.'

# Strings can be added too!
"Hello " + "world!"  # => "Hello world!"
# Strings can be added without using '+'
"Hello " "world!"  # => "Hello world!"

# ... or multiplied
"Hello" * 3  # => "HelloHelloHello"

# A string can be treated like a list of characters
"This is a string"[0]  # => 'T'

# You can find the length of a string
len("This is a string")  # => 16

# String formatting with %
# Even though the % string operator will be deprecated on Python 3.1 and removed
# later at some time, it may still be good to know how it works.
x = 'apple'
y = 'lemon'
z = "The items in the basket are %s and %s" % (x, y)

# A newer way to format strings is the format method.
# This method is the preferred way
"{} is a {}".format("This", "placeholder")
"{0} can be {1}".format("strings", "formatted")
# You can use keywords if you don't want to count.
"{name} wants to eat {food}".format(name="Bob", food="lasagna")

# None is an object
None  # => None

# Don't use the equality "==" symbol to compare objects to None
# Use "is" instead
"etc" is None  # => False
None is None  # => True

# The 'is' operator tests for object identity. This isn't
# very useful when dealing with primitive values, but is
# very useful when dealing with objects.

# Any object can be used in a Boolean context.
# The following values are considered falsey:
#    - None
#    - zero of any numeric type (e.g., 0, 0L, 0.0, 0j)
#    - empty sequences (e.g., '', (), [])
#    - empty containers (e.g., {}, set())
#    - instances of user-defined classes meeting certain conditions
#      see: https://docs.python.org/2/reference/datamodel.html#object.__nonzero__
#
# All other values are truthy (using the bool() function on them returns True).
bool(0)  # => False
bool("")  # => False
# None, 0, 和空字符串都被算作False
# 其他均为True


####################################################
# 2. Variables and Collections
####################################################

# Python has a print statement
print "I'm Python. Nice to meet you!"  # => I'm Python. Nice to meet you!

# Simple way to get input data from console
input_string_var = raw_input(
    "Enter some data: ")  # Returns the data as a string
input_var = input("Enter some data: ")  # Evaluates the data as python code
# Warning: Caution is recommended for input() method usage
# Note: In python 3, input() is deprecated and raw_input() is renamed to input()

# No need to declare variables before assigning to them.
some_var = 5  # Convention is to use lower_case_with_underscores
some_var  # => 5

# Accessing a previously unassigned variable is an exception.
# See Control Flow to learn more about exception handling.
some_other_var  # Raises a name error

# if can be used as an expression
# Equivalent of C's '?:' ternary operator
"yahoo!" if 3 > 2 else 2  # => "yahoo!"

# Lists store sequences
li = []
# You can start with a prefilled list
other_li = [4, 5, 6]

# Add stuff to the end of a list with append
li.append(1)  # li is now [1]
li.append(2)  # li is now [1, 2]
li.append(4)  # li is now [1, 2, 4]
li.append(3)  # li is now [1, 2, 4, 3]
# Remove from the end with pop
li.pop()  # => 3 and li is now [1, 2, 4]
# Let's put it back
li.append(3)  # li is now [1, 2, 4, 3] again.

# Access a list like you would any array
li[0]  # => 1
# Assign new values to indexes that have already been initialized with =
li[0] = 42
li[0]  # => 42
li[0] = 1  # Note: setting it back to the original value
# Look at the last element
li[-1]  # => 3

# Looking out of bounds is an IndexError
li[4]  # Raises an IndexError

# You can look at ranges with slice syntax.
# (It's a closed/open range for you mathy types.)
li[1:3]  # => [2, 4]
# Omit the beginning
li[2:]  # => [4, 3]
# Omit the end
li[:3]  # => [1, 2, 4]
# Select every second entry
li[::2]  # =>[1, 4]
# Reverse a copy of the list
li[::-1]  # => [3, 4, 2, 1]
# Use any combination of these to make advanced slices
# li[start:end:step]

# Remove arbitrary elements from a list with "del"
del li[2]  # li is now [1, 2, 3]

# You can add lists
li + other_li  # => [1, 2, 3, 4, 5, 6]
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
# Note: values for li and for other_li are not modified.
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

# Concatenate lists with "extend()"
li.extend(other_li)  # Now li is [1, 2, 3, 4, 5, 6]

# Remove first occurrence of a value
li.remove(2)  # li is now [1, 3, 4, 5, 6]
li.remove(2)  # Raises a ValueError as 2 is not in the list

# Insert an element at a specific index
li.insert(1, 2)  # li is now [1, 2, 3, 4, 5, 6] again

# Get the index of the first item found
li.index(2)  # => 1
li.index(7)  # Raises a ValueError as 7 is not in the list

# Check for existence in a list with "in"
1 in li  # => True

# Examine the length with "len()"
len(li)  # => 6

# Tuples are like lists but are immutable.
tup = (1, 2, 3)
tup[0]  # => 1
tup[0] = 3  # Raises a TypeError

# You can do all those list thingies on tuples too
len(tup)  # => 3
tup + (4, 5, 6)  # => (1, 2, 3, 4, 5, 6)
tup[:2]  # => (1, 2)
2 in tup  # => True

# You can unpack tuples (or lists) into variables
a, b, c = (1, 2, 3)  # a is now 1, b is now 2 and c is now 3
d, e, f = 4, 5, 6  # you can leave out the parentheses
# Tuples are created by default if you leave out the parentheses
g = 4, 5, 6  # => (4, 5, 6)
# Now look how easy it is to swap two values
e, d = d, e  # d is now 5 and e is now 4

# Dictionaries store mappings
empty_dict = {}
# Here is a prefilled dictionary
filled_dict = {"one": 1, "two": 2, "three": 3}

# Look up values with []
filled_dict["one"]  # => 1

# Get all keys as a list with "keys()"
filled_dict.keys()  # => ["three", "two", "one"]
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
# Note - Dictionary key ordering is not guaranteed.
# Your results might not match this exactly.
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

# Get all values as a list with "values()"
filled_dict.values()  # => [3, 2, 1]
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
# Note - Same as above regarding key ordering.
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

# Get all key-value pairs as a list of tuples with "items()"
filled_dicts.items()  # => [("one", 1), ("two", 2), ("three", 3)]

!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
# Note -Check for existence of keys in a dictionary with "in"
"one" in filled_dict  # => True
1 in filled_dict  # => False
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

# Looking up a non-existing key is a KeyError
filled_dict["four"]  # KeyError

# Use "get()" method to avoid the KeyError
filled_dict.get("one")  # => 1
filled_dict.get("four")  # => None
# Note: The get method supports a default argument when the value is missing
filled_dict.get("one", 4)  # => 1
filled_dict.get("four", 4)  # => 4
# Note： that filled_dict.get("four") is still => None
# Note：(get doesn't set the value in the dictionary)

# set the value of a key with a syntax similar to lists
filled_dict["four"] = 4  # now, filled_dict["four"] => 4

# Note："setdefault()" inserts into a dictionary only if the given key isn't present
filled_dict.setdefault("five", 5)  # filled_dict["five"] is set to 5
filled_dict.setdefault("five", 6)  # filled_dict["five"] is still 5

# Note：Sets就是集合了字典和list，但是没有字典里的value，而且不像list里面的数值可以重复，而且sets里面的元素和dict一样死无序的。
# Note：Sets store ... well sets (which are like lists but can contain no duplicates)
empty_set = set()
# Initialize a "set()" with a bunch of values
some_set = set([1, 2, 2, 3, 4])  # some_set is now set([1, 2, 3, 4])

# Note：order is not guaranteed, even though it may sometimes look sorted
another_set = set([4, 3, 2, 2, 1])  # another_set is now set([1, 2, 3, 4])

# 和字典表示方式类似，但是没有value
# Since Python 2.7, {} can be used to declare a set
filled_set = {1, 2, 2, 3, 4}  # => {1, 2, 3, 4}

# Add more items to a set
filled_set.add(5)  # filled_set is now {1, 2, 3, 4, 5}

# Do set intersection with &
other_set = {3, 4, 5, 6}
filled_set & other_set  # => {3, 4, 5}

# Do set union with |
filled_set | other_set  # => {1, 2, 3, 4, 5, 6}

# Do set difference with -
{1, 2, 3, 4} - {2, 3, 5}  # => {1, 4}

# Do set symmetric difference with ^
{1, 2, 3, 4} ^ {2, 3, 5}  # => {1, 4, 5}

# Check if set on the left is a superset of set on the right
{1, 2} >= {1, 2, 3}  # => False

# Check if set on the left is a subset of set on the right
{1, 2} <= {1, 2, 3}  # => True

# Check for existence in a set with in
2 in filled_set  # => True
10 in filled_set  # => False


####################################################
#  3. Control Flow
####################################################

# Let's just make a variable
some_var = 5

# Here is an if statement. Indentation is significant in python!
# prints "some_var is smaller than 10"
if some_var > 10:
    print "some_var is totally bigger than 10."
elif some_var < 10:  # This elif clause is optional.
    print "some_var is smaller than 10."
else:  # This is optional too.
    print "some_var is indeed 10."

"""
For loops iterate over lists
prints:
    dog is a mammal
    cat is a mammal
    mouse is a mammal
"""
for animal in ["dog", "cat", "mouse"]:
    # You can use {0} to interpolate formatted strings. (See above.)
    print "{0} is a mammal".format(animal)

"""
"range(number)" returns a list of numbers
from zero to the given number
prints:
    0
    1
    2
    3
"""
for i in range(4):
    print i

"""
"range(lower, upper)" returns a list of numbers
from the lower number to the upper number
prints:
    4
    5
    6
    7
"""
for i in range(4, 8):
    print i

"""
While loops go until a condition is no longer met.
prints:
    0
    1
    2
    3
"""
x = 0
while x < 4:
    print x
    x += 1  # Shorthand for x = x + 1

# Handle exceptions with a try/except block

# Works on Python 2.6 and up:
try:
    # Use "raise" to raise an error
    raise IndexError("This is an index error")
except IndexError as e:
    pass  # Pass is just a no-op. Usually you would do recovery here.
except (TypeError, NameError):
    pass  # Multiple exceptions can be handled together, if required.
else:  # Optional clause to the try/except block. Must follow all except blocks
    print "All good!"  # Runs only if the code in try raises no exceptions
finally:  # Execute under all circumstances
    print "We can clean up resources here"

# Instead of try/finally to cleanup resources you can use a with statement
with open("myfile.txt") as f:
    for line in f:
        print line


####################################################
# 4. Functions
####################################################

# Use "def" to create new functions
def add(x, y):
    print "x is {0} and y is {1}".format(x, y)
    return x + y  # Return values with a return statement


# Calling functions with parameters
add(5, 6)  # => prints out "x is 5 and y is 6" and returns 11

# Another way to call functions is with keyword arguments
add(y=6, x=5)  # Keyword arguments can arrive in any order.

# Note：
# You can define functions that take a variable number of
# positional args, which will be interpreted as a tuple by using *
def varargs(*args):
    return args


varargs(1, 2, 3)  # => (1, 2, 3)

Note：
# You can define functions that take a variable number of
# keyword args, as well, which will be interpreted as a dict by using **
def keyword_args(**kwargs):
    return kwargs


# Let's call it to see what happens
keyword_args(big="foot", loch="ness")  # => {"big": "foot", "loch": "ness"}


# You can do both at once, if you like
def all_the_args(*args, **kwargs):
    print args
    print kwargs


"""
all_the_args(1, 2, a=3, b=4) prints:
    (1, 2)
    {"a": 3, "b": 4}
"""

# Note：
# When calling functions, you can do the opposite of args/kwargs!
# Use * to expand positional args and use ** to expand keyword args.
args = (1, 2, 3, 4)
kwargs = {"a": 3, "b": 4}
all_the_args(*args)  # equivalent to foo(1, 2, 3, 4)
all_the_args(**kwargs)  # equivalent to foo(a=3, b=4)
all_the_args(*args, **kwargs)  # equivalent to foo(1, 2, 3, 4, a=3, b=4)


# you can pass args and kwargs along to other functions that take args/kwargs
# by expanding them with * and ** respectively
def pass_all_the_args(*args, **kwargs):
    all_the_args(*args, **kwargs)
    print varargs(*args)
    print keyword_args(**kwargs)



# Note：全局变量和局部变量
# Function Scope
x = 5


def set_x(num):
    # Note：
    # Local var x not the same as global variable x
    x = num  # => 43
    print x  # => 43


def set_global_x(num):
    global x
    print x  # => 5
    x = num  # global var x is now set to 6
    print x  # => 6


set_x(43)
set_global_x(6)


# Python has first class functions
def create_adder(x):
    def adder(y):
        return x + y

    return adder


add_10 = create_adder(10)
add_10(3)  # => 13

# There are also anonymous functions
(lambda x: x > 2)(3)  # => True
(lambda x, y: x ** 2 + y ** 2)(2, 1)  # => 5

# There are built-in higher order functions
map(add_10, [1, 2, 3])  # => [11, 12, 13]
map(max, [1, 2, 3], [4, 2, 1])  # => [4, 2, 3]

filter(lambda x: x > 5, [3, 4, 5, 6, 7])  # => [6, 7]

# We can use list comprehensions for nice maps and filters
[add_10(i) for i in [1, 2, 3]]  # => [11, 12, 13]
[x for x in [3, 4, 5, 6, 7] if x > 5]  # => [6, 7]

# You can construct set and dict comprehensions as well.
{x for x in 'abcddeef' if x in 'abc'}  # => {'a', 'b', 'c'}
{x: x ** 2 for x in range(5)}  # => {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}


####################################################
# 5. Classes
####################################################

# We subclass from object to get a class.
class Human(object):
    # A class attribute. It is shared by all instances of this class
    species = "H. sapiens"

    # Basic initializer基本构造函数, this is called when this class is instantiated.
    # Note that the double leading and trailing underscores denote objects
    # or attributes that are used by python but that live in user-controlled
    # namespaces. You should not invent such names on your own.
    def __init__(self, name):# Basic initializer基本构造函数
        # Assign the argument to the instance's name attribute
        # 将参数赋给对象成员属性
        self.name = name

        # Initialize property
        self.age = 0

    # An instance method. All methods take "self" as the first argument，成员方法
    def say(self, msg):
        return "{0}: {1}".format(self.name, msg)

    # A class method is shared among all instances
    # They are called with the calling class as the first argument
    # Note：这类方法在调用时，会把类本身传给第一个参数
    @classmethod
    def get_species(cls):
        return cls.species

    # A static method is called without a class or instance reference
    # Note：静态方法是不需要类和对象的引用就可以调用的方法
    @staticmethod
    def grunt():
        return "*grunt*"
        
    # 私有方法
    # A property is just like a getter.
    # It turns the method age() into an read-only attribute
    # of the same name.
    @property
    def age(self):
        return self._age

    # This allows the property to be set
    @age.setter
    def age(self, age):
        self._age = age

    # This allows the property to be deleted
    @age.deleter
    def age(self):
        del self._age


# Instantiate a class
i = Human(name="Ian")
print i.say("hi")  # prints out "Ian: hi"

j = Human("Joel")
print j.say("hello")  # prints out "Joel: hello"

# Call our class method
i.get_species()  # => "H. sapiens"

# Change the shared attribute
Human.species = "H. neanderthalensis"
i.get_species()  # => "H. neanderthalensis"
j.get_species()  # => "H. neanderthalensis"

# Call the static method，Note：不需要类和对象的引用
Human.grunt()  # => "*grunt*"

# Update the property
i.age = 42

# Get the property
i.age  # => 42

# Delete the property
del i.age
i.age  # => raises an AttributeError

####################################################
# 6. Modules
####################################################

# You can import modules
import math

print math.sqrt(16)  # => 4

# You can get specific functions from a module
from math import ceil, floor

print ceil(3.7)  # => 4.0
print floor(3.7)  # => 3.0

# You can import all functions from a module.
# Warning: this is not recommended
from math import *

# You can shorten module names
import math as m

math.sqrt(16) == m.sqrt(16)  # => True
# you can also test that the functions are equivalent
from math import sqrt

math.sqrt == m.sqrt == sqrt  # => True

# Python modules are just ordinary python files. You
# can write your own, and import them. The name of the
# module is the same as the name of the file.

# You can find out which functions and attributes
# defines a module.
import math

dir(math)


# If you have a Python script named math.py in the same
# folder as your current script, the file math.py will
# be loaded instead of the built-in Python module.
# This happens because the local folder has priority
# over Python's built-in libraries.


####################################################
# 7. Advanced
####################################################

# Generators
# 列表生成式
>>> L = [x * x for x in range(10)]
>>> L
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
此时我们创建的是一个对象，实际存在的列表，因此列表的容量收到了内存大小的限制，而且，我们创建一个包含100万个元素的列表，不仅占用很大的存储空间，如果我们仅仅需要访问前面几个元素，那么后面绝大多数元素占用的空间都白白浪费了，所以如果列表元素可以按照某种算法推算出来，那么我么可以在循环的过程中不断推算出后续的元素，这样就不必创建完整的list，从而节省大量的空间。
所谓生成器就是，这种一边循环一边计算的机制。

第一种表示方法：只需把列表生成式的【】改成（）即可
>>> g = (x * x for x in range(10))
>>> g
<generator object <genexpr> at 0x104feab40>
创建L和g的区别仅在于最外层的[]和()，L是一个list，而g是一个generator。

如果要一个一个打印出来，可以通过generator的next()方法：
>>> g.next()
0
>>> g.next()
1
>>> g.next()
4
>>> g.next()
9
Note:generator保存的是算法，每次调用next()，就计算出下一个元素的值，直到计算到最后一个元素，没有更多的元素时，抛出StopIteration的错误。
正确的方法是使用for循环，因为generator也是可迭代对象：
>>> g = (x * x for x in range(10))
>>> for n in g:
...     print n
...
0
1
···

著名的斐波拉契数列（Fibonacci），除第一个和第二个数外，任意一个数都可由前两个数相加得到：
1, 1, 2, 3, 5, 8, 13, 21, 34, ...
斐波拉契数列用列表生成式写不出来，但是，用函数把它打印出来却很容易：

def fib(max):
    n, a, b = 0, 0, 1
    while n < max:
        print b
        a, b = b, a + b
        n = n + 1
可以看出，fib函数实际上是定义了斐波拉契数列的推算规则，可以从第一个元素开始，推算出后续任意的元素，这种逻辑其实非常类似generator。

第二种表示方法：要把fib函数变成generator，只需要把print b改为yield b就可以了：

def fib(max):
    n, a, b = 0, 0, 1
    while n < max:
        yield b
        a, b = b, a + b
        n = n + 1

>>> fib(6)
<generator object fib at 0x104feaaa0>

这里，最难理解的就是generator和函数的执行流程不一样。函数是顺序执行，遇到return语句或者最后一行函数语句就返回。而变成generator的函数，在每次调用next()的时候执行，遇到yield语句返回并且打印出来，程序暂停，再次执行时从上次返回打印的yield语句处继续执行。这样就形成了一边循环一边产生数据的形式。

举个简单的例子，定义一个generator，依次返回数字1，3，5：

>>> def odd():
...     print 'step 1'
...     yield 1
...     print 'step 2'
...     yield 3
...     print 'step 3'
...     yield 5
...
>>> o = odd()
>>> o.next()
step 1
1
>>> o.next()
step 2
3
>>> o.next()
step 3
5
>>> o.next()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
StopIteration
可以看到，odd不是普通函数，而是generator，在执行过程中，遇到yield就中断，下次又继续执行。执行3次yield后，已经没有yield可以执行了，所以，第4次调用next()就报错。

回到fib的例子，我们在循环过程中不断调用yield，就会不断中断。当然要给循环设置一个条件来退出循环，不然就会产生一个无限数列出来。

同样的，把函数改成generator后，我们基本上从来不会用next()来调用它，而是直接使用for循环来迭代：

>>> for n in fib(6):
...     print n
...
1
1
2
3
5
8

要理解generator的工作原理，它是在for循环的过程中不断计算出下一个元素，并在适当的条件结束for循环。对于函数改成的generator来说，遇到return语句或者执行到函数体最后一行语句，就是结束generator的指令，for循环随之结束。


# A generator "generates" values as they are requested instead of storing
# everything up front，生成器就是产生需要被用到的值，而不是在
# 程序的开始阶段就生成所有需要用的数据存储起来，这样可以节省大量空间

# The following method (*NOT* a generator) will double all values and store it
# in `double_arr`. For large size of iterables, that might get huge!
def double_numbers(iterable):
    double_arr = []
    for i in iterable:
        double_arr.append(i + i)
    return double_arr


# Running the following would mean we'll double all values first and return all
# of them back to be checked by our condition
for value in double_numbers(range(1000000)):  # `test_non_generator`
    print value
    if value > 5:
        break


# We could instead use a generator to "generate" the doubled value as the item
# is being requested
def double_numbers_generator(iterable):
    for i in iterable:
        yield i + i


# Running the same code as before, but with a generator, now allows us to iterate
# over the values and doubling them one by one as they are being consumed by
# our logic. Hence as soon as we see a value > 5, we break out of the
# loop and don't need to double most of the values sent in (MUCH FASTER!)
for value in double_numbers_generator(xrange(1000000)):  # `test_generator`
    print value
    if value > 5:
        break

# BTW:（By the way） did you notice the use of `range` in `test_non_generator` and `xrange` in `test_generator`?
# Just as `double_numbers_generator` is the generator version of `double_numbers`
# We have `xrange` as the generator version of `range`
# `range` would return back and array with 1000000 values for us to use
！！！！！！！！！！！！！！！！！！！！！！！！！！！
# `xrange` would generate 1000000 values for us as we request / iterate over those items

# Just as you can create a list comprehension, you can create generator
# comprehensions as well.
values = (-x for x in [1, 2, 3, 4, 5])
for x in values:
    print(x)  # prints -1 -2 -3 -4 -5 to console/terminal

# You can also cast a generator comprehension directly to a list.
values = (-x for x in [1, 2, 3, 4, 5])
gen_to_list = list(values)
print(gen_to_list)  # => [-1, -2, -3, -4, -5]

# Decorators

文件名：HELLO.PY
def hello(fn):
    def wrapper():
        print "hello, %s" % fn.__name__
        fn()
        print "goodby, %s" % fn.__name__
    return wrapper
 
@hello
def foo():
    print "i am foo"
 
foo()

当你运行代码，你会看到如下输出：
[chenaho@chenhao-air]$ python hello.py
hello, foo
i am foo
goodby, foo

你可以看到如下的东西：
1）函数foo前面有个@hello的“注解”，hello就是我们前面定义的函数hello
2）在hello函数中，其需要一个fn的参数（这就用来做回调的函数）
3）hello函数中返回了一个inner函数wrapper，这个wrapper函数回调了传进来的fn，并在回调前后加了两条语句。

Decorator 的本质
对于Python的这个@注解语法糖- Syntactic Sugar 来说，当你在用某个@decorator来修饰某个函数func时，如下所示:
@decorator
def func():
    pass
    
其解释器会解释成下面这样的语句：
func = decorator(func)

尼玛，这不就是把一个函数当参数传到另一个函数中，然后再回调吗？是的，但是，我们需要注意，那里还有一个赋值语句，把decorator这个函数的返回值赋值回了原来的func。 根据《函数式编程》中的first class functions中的定义的，你可以把函数当成变量来使用，所以，decorator必需得返回了一个函数出来给func，这就是所谓的higher order function 高阶函数，不然，后面当func()调用的时候就会出错。 就我们上面那个hello.py里的例子来说，

@hello
def foo():
    print "i am foo"
被解释成了：

foo = hello(foo)
是的，这是一条语句，而且还被执行了。你如果不信的话，你可以写这样的程序来试试看：

def fuck(fn):
    print "fuck %s!" % fn.__name__[::-1].upper()
 
@fuck
def wfg():
    pass
没了，就上面这段代码，没有调用wfg()的语句，你会发现， fuck函数被调用了，而且还很NB地输出了我们每个人的心声！

再回到我们hello.py的那个例子，我们可以看到，hello(foo)返回了wrapper()函数，所以，foo其实变成了wrapper的一个变量，而后面的foo()执行其实变成了wrapper()。

知道这点本质，当你看到有多个decorator或是带参数的decorator，你也就不会害怕了。

比如：多个decorator

@decorator_one
@decorator_two
def func():
    pass
相当于：

func = decorator_one(decorator_two(func))
比如：带参数的decorator：

@decorator(arg1, arg2)
def func():
    pass
相当于：

func = decorator(arg1,arg2)(func)
这意味着decorator(arg1, arg2)这个函数需要返回一个“真正的decorator”。


# A decorator is a higher order function, which accepts and returns a function.
# Simple usage example – add_apples decorator will add 'Apple' element into
# fruits list returned by get_fruits target function.
def add_apples(func):
    def get_fruits():
        fruits = func()
        fruits.append('Apple')
        return fruits
    return get_fruits

@add_apples
def get_fruits():  # == get-fruits = add_apples(get_fruits)
    return ['Banana', 'Mango', 'Orange']

# Prints out the list of fruits with 'Apple' element in it:
# Banana, Mango, Orange, Apple
### str.join（）只适用于字符串，可以利用sep参数给print函数传递分隔的信息
print ', '.join(get_fruits())
等效于
s = (get_fruits())
print(*s, sep='，')

# in this example beg wraps say
# Beg will call say. If say_please is True then it will change the returned
# message
from functools import wraps

def beg(target_function):
    @wraps(target_function)
    def wrapper(*args, **kwargs):
        msg, say_please = target_function(*args, **kwargs)
        if say_please:
            return "{} {}".format(msg, "Please! I am poor :(")
        return msg

    return wrapper


@beg
def say(say_please=False):
    msg = "Can you buy me a beer?"
    return msg, say_please


print say()  # Can you buy me a beer?
print say(say_please=True)  # Can you buy me a beer? Please! I am poor :(
```

## Ready For More?

### Free Online

* [Automate the Boring Stuff with Python](https://automatetheboringstuff.com)
* [Learn Python The Hard Way](http://learnpythonthehardway.org/book/)
* [Dive Into Python](http://www.diveintopython.net/)
* [The Official Docs](http://docs.python.org/2/)
* [Hitchhiker's Guide to Python](http://docs.python-guide.org/en/latest/)
* [Python Module of the Week](http://pymotw.com/2/)
* [A Crash Course in Python for Scientists](http://nbviewer.ipython.org/5920182)
* [First Steps With Python](https://realpython.com/learn/python-first-steps/)
* [LearnPython](http://www.learnpython.org/)
* [Fullstack Python](https://www.fullstackpython.com/)

### Dead Tree

* [Programming Python](http://www.amazon.com/gp/product/0596158106/ref=as_li_qf_sp_asin_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=0596158106&linkCode=as2&tag=homebits04-20)
* [Dive Into Python](http://www.amazon.com/gp/product/1441413022/ref=as_li_tf_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=1441413022&linkCode=as2&tag=homebits04-20)
* [Python Essential Reference](http://www.amazon.com/gp/product/0672329786/ref=as_li_tf_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=0672329786&linkCode=as2&tag=homebits04-20)


