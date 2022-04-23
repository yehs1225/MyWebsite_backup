# Function

function基本上是將一些操作包裝在一起來執行特定功能。

## 必要元素

- 用`def`開頭定義一個function。
- 若想要之後再定義內容，可先寫入`pass`，就不會讓這個空的function出現錯誤。
- 呼叫function要加上`()`。

```python
def hello_func():
    pass

# execute the function
print(hello_func())
# None （since no value returned）

# call function itself
print(hello_func)
# <function hello_func at 0x0000021604F2F040>
```

## Arguments

基本上使用function的人，不需要詳細知道內部如何運作，只需要知道 **輸入**和 **輸出** 是什麼就行了。而輸入的參數我們就稱為arguments（下面範例就是指`greeting`）。

```python
def hello_func(greeting):
    return '{} Function.'.format(greeting)

print(hello_func('Hi'))
```

### Default arguments

若function要求要輸入arguments，沒有輸入的話就會出現error。但是也可以設定default值，當沒有輸入時就將變數設定為該值（下面範例就是指`name`）。

```python
def hello_func(greeting = 'Hi'):
    return '{}, {}'.format(greeting)

print(hello_func())
```

### Position arguments

指的是當呼叫函式時，傳入的 arguments的**位置**是最重要的。

例如你本來是想輸出 「Hi, John」，但因為輸入時未注意傳入參數順序（位置），所以function理所當然地依照順序接收arguments。

```python
def hello_func(greeting, name):
    return '{}, {}'.format(greeting, name)

print(hello_func('John', 'Hi'))
# John, Hi
```

### Keyword arguments

相對於position arguments，keyword arguments因為有keyword附著在每一個argument上，所以就不需要在意位置關係。

```python
def hello_func(greeting, name):
    return '{}, {}'.format(greeting, name)

print(hello_func(name='John', greeting='Hi'))
```

### *args & **kwargs

一般看到別人寫的function都會有這兩個arguments，因為代表可以接收 **任意數量**的arguments。

`args`是position arguments的縮寫，會是一**tuple**。

`kwargs`是keyword arguments的縮寫，會是一**dictionary**。

```python
def student_info(*args, **kwargs):
    print(args)
    print(kwargs)
	# ('Math', 'Art')
	# {'name': 'John', 'age': 21}
    
student_info('Math', 'Art', name='John', age=21)
```

#### Unpacked

`*list`、`**dictionary`代表unpacked，因此我們可以在傳入function時利用這個技巧。

```python
def student_info(*args, **kwargs):
    print(args)
    print(kwargs)

courses = ['Math', 'Art']
info = {'name': 'John', 'age': 21}

student_info(*courses, **info)
```

