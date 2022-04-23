# Additional Materials

## libaries, packages , modules, framework差異

### Modules

幫助你的code變得更有組織性，也就是將相關的code打包在一起，讓你可以在其他地方import進來使用。可以說module就是 **一綑相關的程式碼被儲存在附檔名為`.py`**。裡面可以是function, classes, or variables。

一些常用的modules : random, datetime, re。

**Ex**

- 有一檔案 < hello.py >內含一function `hello_message`


```python
def hello_message(msg):
    print('Hello, {}'.format(msg))
```

- 在其他檔案中import

此外，`module.__file__`可以找到該module的所在位置。

```python
# import method 1
import hello

hello.hello_message('World')

#import method 2
from hello import hello_message

hello_message('World')
```

### Packages

若開發較大專案，可能會有很多不同modules，造成管理上的困難。因此 packages就是 **一個資料夾裡面蒐集了多個modules**，允許module namespace有 **階層架構**，就像一般在資料夾中也能有子資料夾，也可以將modules組織成packages和subpackages。

一些常用的packages : Numpy, pandas

**Ex**

package結構及引入方式

```bash
├── my_module
│   ├── __init__.py
│   ├── training
│   │   ├── __init__.py
│   │   ├── training.py
│   │   ├── loss.py
│   │   └── test.py
│   ├── submission
│   │   ├── __init__.py
│   │   ├── submit.py
│   │   ├── production.py
│   │   └── test.py
```

```python
# import method 1
import my_model.training.loss

#import method 2
from my_model.training import loss
```

### Libraries

通常說library包含許多modules和packages成為一個可重複利用的程式碼塊。但因為Package本身也可以包含很多subpackages，所以Library有時也會和Packages互換使用。一般來說，還是較常稱 **package包含許多modules；Library包含許多packages**。

常用的像是 : Matplotlib, Beautiful Soup。

packages提到的Numpy, pandas也會被稱作Library

### Framework

跟library很像，包含很多modules跟packages幫助使用者執行特定程序，加快開發流程，但framework比library複雜得多。framework包含該應用程式基本的流程和架構。

常用的framework有Django和Flask。

## Dunder or Magic method

在python中dunder method 也稱為 magic method，指的是用前後`__`包裹住的method name。Dunder = Double Under（Underscores）。常用來作為operator overloading使用。一些範例像是 : `__init__`、`__add__`、`__len__`、`__repre__`等等。

> #### operator overloading 
>
> 是多型（polymorphism）的一種，多行指的是位不同資料類型的實體提供統一的介面，或使用單一符號表是多個不同的類型。例如 : + 在Python可作用於 字串 和 數值上，且表現行為也會跟著調整，字串像是拼接、數值則是像 一般計算的方法。



## Function Annotations

Python 3的函式註解，讓你在定義參數時對參數和返回值添加註解。

```python
def foo(a: int, b: "this is b", c: str = 5) -> tuple:
    return a, b, c
```

- `a: int` 是參數註解
- `c: str = 5`是有default值的參數註解
- `-> tuple`是回傳值的註解

可以用`__annotations__`來得到

```python
foo.__annotations__
```

## Booleans

###  is

比較**內容**的相異性用的是`==`；而`is`是用來比較**記憶體**位置是否相同。

```python
a = [1, 2, 3]
b = [1, 2, 3]

print(a == b)
# True

print(a is b)
# False

# Print the memory location
print(id(a))
print(id(b))
# 1679406415360
# 1679409529472
```

```python
a = [1, 2, 3]
b = a

print(a is b)
# True
```

### False Value

- False
- None
- Zero of any numeric type.
- Any empty sequence. （e.g. `''`、`()`、`[]`）
- Any empty mapping. （e.g.`{}`）

## Loops

### break&continue

`break` : 離開迴圈。

`continue` : 直接進入下一迴圈。

```python
nums = [1, 2, 3]

for num in nums:
    if num == 2:
        print("Found!")
        break
    print(num)
    # 1
    # found!
    
for num in nums:
    if num == 2:
        print("Found!")
        continue
    print(num)
    # 1
    # Found!
    # 3
```



