---
title: Iterators, Generators, and Classic Coroutines
---

- Every standard collection in Python is iterable. 
- An iterable is an object that provides an iterator
{: .msg-info }
- A common cause of errors in building iterables and iterators is to confuse the two. 
  - iterables have an __iter__ method that instantiates a new iterator every time. 
  - Iterators implement a __next__ method that returns individual items, and an __iter__ method that returns self.
{: .msg-info }


- [Implement a Sentence Iterator class using __get_item__](https://github.com/devignitelab/python-hack/blob/main/training/80-advanced-iter/iter-words.py){: .blank}
  - `findall` returns a list with all nonoverlapping matches of the regular expression, as a list of strings.
  - `self.words` holds the result of .findall, so we simply return the word at the given index.
  - To complete the sequence protocol, we implement `__len__` although it is not needed to make an iterable.
  - `reprlib.repr` is a utility function to generate abbreviated string representations of data structures that can be very large

- Why Sequences are Iterable. The `iter` Function
  - Whenever Python needs to iterate over an object x, it automatically calls `iter(x)`
  - The `iter` built-in function:
    - Checks whether the object implements `__iter__`, and calls that to obtain an iterator.
    - If `__iter__` is not implemented, but `__getitem__` is, then `iter()` creates an iterator that tries to fetch items by index, starting from 0 (zero).
    - If that fails, Python raises `TypeError`, usually saying 'C' object is not iterable, where C is the class of the target object.

- Using `iter` with a `Callable`
  - [Sample](https://github.com/devignitelab/python-hack/blob/main/training/80-advanced-iter/iter-with-func.py){: .blank}
  - We can call `iter()` with two arguments to create an iterator from a function or any `callable object`
  - In this usage, the `first argument` must be a callable to be invoked repeatedly (with no arguments)
    to produce values, and the second argument is a `sentinel`
  - `sentinel` a marker value which, when returned by the callable, causes the iterator to raise `StopIteration` instead of yielding the sentinel.
  - E.g. In below code the iteration will happen until the `randint` value output a `1` which is a `snetinel` passed as second argument of
    `iter(d6,1)` function
    ```bash
    def d6():
      return randint(1, 6)

    d6_iter = iter(d6, 1)

    for roll in d6_iter:
        print(roll)
    ```
- `Iterator` source code
  ![](/assets/images/python/iter_source.PNG)
    - `__subclasshook__` supports structural type checks with isinstance and issubclass.
    - `_check_methods` traverses the `__mro__` of the class to check whether the methods are implemented in its base classes.
      If the methods are implemented, the C class will be recognized as a virtual subclass of Iterator. In other words, `issubclass(C, Iterable)` will return True.

- [Implement Iterator using ABC.Iterator](https://github.com/devignitelab/python-hack/blob/main/training/80-advanced-iter/iter-custom.py){: .blank }

- [Implement Iterator Generator](https://github.com/devignitelab/python-hack/blob/main/training/80-advanced-iter/iter-using-yield.py){: .blank}
  - Any Python function that has the yield keyword in its body is a generator function: a function which, when called, returns a generator object. In other words, a generator function is a generator factory.

- [Implement Iterator Generator with iterable Source ](https://github.com/devignitelab/python-hack/blob/main/training/80-advanced-iter/iter-source-iterable.py){: .blank}


---
- [Itertools Functions](https://docs.python.org/3/library/itertools.html)