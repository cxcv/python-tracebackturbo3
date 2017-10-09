tracebackturbo3
===============
A drop-in replacement for the python3 [traceback module](http://docs.python.org/library/traceback.html)
that enables dumping of the local variable scope aside normal stack traces.

Usage
-----
```python3
import tracebackturbo as traceback

def erroneous_function():
    ham = u"unicode string with umlauts äöü."
    eggs = "binary string with umlauts äöü."
    i = 23
    if i>5:
        raise Exception("it's a trap!")

try:
    erroneous_function()
except:
    print(traceback.format_exc())
```

Sample Output
-------------
This is the output of tracebackturbo:
```
Traceback (most recent call last):
  File "test.py", line 13, in <module>
    erroneous_function()
    __builtins__ = <module 'builtins' (built-in)>
    __cached__ = None
    __doc__ = None
    __file__ = 'test.py'
    __loader__ = <_frozen_importlib.SourceFileLoader object at 0x7f894df73c18>
    __name__ = '__main__'
    __package__ = None
    __spec__ = None
    erroneous_function = <function erroneous_function at 0x7f894df77bf8>
    traceback = <module 'tracebackturbo' from '/srv/home/cxcv/Dropbox/home/git/python-tracebackturbo3/tracebackturbo.py'>
  File "test.py", line 10, in erroneous_function
    raise Exception("it's a trap!")
    eggs = 'binary string with umlauts äöü.'
    ham = 'unicode string with umlauts äöü.'
    i = 23
Exception: it's a trap!
```

versus the normal output:
```
Traceback (most recent call last):
  File "test.py", line 14, in <module>
    erroneous_function()
  File "test.py", line 11, in erroneous_function
    raise Exception("it's a trap!")
Exception: it's a trap!
```

Python2
-------
See [https://github.com/cxcv/python-tracebackturbo2](https://github.com/cxcv/python-tracebackturbo2)

License & Credit
-----------------
This code is based upon the original traceback module that ships with stock
python. This modules used the [Python License](http://www.opensource.org/licenses/Python-2.0).