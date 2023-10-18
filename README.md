# i promise to maybe write tests 🧪
## Specifically within jupyter notebooks which is my goto IDE now.
How I'm going to maybe write code that breaks less.


#### Step 1, make modules in cells using %%writefile
```python
%%writefile something.py

def something_fun(x):

    if type(x) is str:
      return str(int(x)+2)

    if x is None:
      return None
    return x + 2
```


#### Step 2, write tests in a cell in the pytest format, and save to test_.py files with  %%writefile
```python
%%writefile test_main.py

import something

def test_answer():
    assert something.something_fun(3) == 5

def test_answer2():
    assert something.something_fun(9) == 11

def test_answer3():
    assert something.something_fun(-2) == 0

def test_answer4():
    assert something.something_fun(None) == None

def test_answer_str():
    assert something.something_fun('7') == '9'

```

#### Step 4, Run tests using pytest (again running in a cell)
```python
!pytest
```

#### Step 5, Load the module using importlib.reload to allow for interactive devlopment without restarting notebook
```python
import something

from importlib import reload
reload(something)

print(something.something_fun(7))

print(something.something_fun('-2'))
```
