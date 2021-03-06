# python 学习

### python 基础

#### 数据类型有变量

- **整数**     -       python 整数很大时允许数字中间以 ```_``` 分格，其余与数学上的写法一样
- **浮点数** -       小数，可用科学计算法表示，整数运算永远是精确的，包括除法，浮点运算有四舍五入的误差 ?
- **字符串** -       字符串可用 ```r'string'``` 来表示string不转义；允许'''...string ''' 表示多行内容；多行字符串`'''...'''`还可以在前面加上`r`使用，f' {}' 格式化字符串
- **布尔值** -       `True 、False` 两个值，可用```and 、or、 not```运算
- **空值**     -      ``` None```表示，```None``` 不能理解为```0```，因为 ``` 0 ```是有意义的，而```None``` 是一个特殊的空值
- **变量**     -      变量的概念基本上和初中代数的方程变量是一致的，只是在算机程序中，变量不仅可以是数字，还可以是任意数据类型。变量在程序中就是用一个变量名表示了，变量名必须是大小写英文、数字和`_`的组合，且不能用数字开头
- **常量**     -       通常用全部大写表示常量

**除法**： `/`除法计算结果是浮点数，即使是两个整数恰好整除，结果也是浮点数

​			还有一种除法是`//`，称为地板除，两个整数的除法仍然是整数:

```python
>>> 10 // 3
3
>>> 9 / 3
3.0

```

### 字符编码

因为计算机只能处理数字，如果要处理文本，就必须先把文本转换为数字才能处理。最早的计算机在设计时采用8个比特（bit）作为一个字节（byte），所以，一个字节能表示的最大的整数就是255（二进制11111111=十进制255），如果要表示更大的整数，就必须用更多的字节。比如两个字节可以表示的最大整数是`65535`，4个字节可以表示的最大整数是`4294967295`。

由于计算机是美国人发明的，因此，最早只有127个字符被编码到计算机里，也就是大小写英文字母、数字和一些符号，这个编码表被称为`ASCII`编码，比如大写字母`A`的编码是`65`，小写字母`z`的编码是`122`。

但是要处理中文显然一个字节是不够的，至少需要两个字节，而且还不能和ASCII编码冲突，所以，中国制定了`GB2312`编码，用来把中文编进去。

Unicode把所有语言都统一到一套编码里，这样就不会再有乱码问题了。

字母`A`用ASCII编码是十进制的`65`，二进制的`01000001`；

字符`0`用ASCII编码是十进制的`48`，二进制的`00110000`，注意字符`'0'`和整数`0`是不同的；

汉字`中`已经超出了ASCII编码的范围，用Unicode编码是十进制的`20013`，二进制的`01001110 00101101`。

你可以猜测，如果把ASCII编码的`A`用Unicode编码，只需要在前面补0就可以，因此，`A`的Unicode编码是`00000000 01000001`

如果统一成Unicode编码，乱码问题从此消失了。但是，如果你写的文本基本上全部是英文的话，用Unicode编码比ASCII编码需要多一倍的存储空间，在存储和传输上就十分不划算。

所以，本着节约的精神，又出现了把Unicode编码转化为“可变长编码”的`UTF-8`编码。UTF-8编码把一个Unicode字符根据不同的数字大小编码成1-6个字节，常用的英文字母被编码成1个字节，汉字通常是3个字节，只有很生僻的字符才会被编码成4-6个字节。如果你要传输的文本包含大量英文字符，用UTF-8编码就能节省空间：

#### 数组与元组

数组可增删改查[] 初始化，元组用()括号初始化，初始化之后就不能修改

**数组** - 元素可为任意类型的值

- `len(arr)` 长度
- `arr[index] `获取指定索引值，`arr[-1] = arr[len(arr)-1]`
- `arr.append( e)`尾部追加
- `arr.insert(index,e)`
- `arr.pop()` 删除尾部元素
- `arr.pop(index)` 删除指定位置元素
- `arr[index] = e, replace`

**元组** 

元组需要注意的是初始化一个长度为1的的元组时，会有陷阱.`()` 运算符既可以表示`tuple`元组又可以表示数学公式的小括号，这就产生歧义如下:

```  py
>>> t=(1)
>>> 1
>>> t=(1,)
>>> (1,)
>>> a = ()
>>> ()
```

### 条件判断

if ...:

 elif....:

else:

**循环：**

- for x in arr:  
- for x in range(101)

**dict**

``` python
a= {'x':1}
a['key'] = value

>>>  key in a: // 判断dict a 是否存在key
    a.get(key, defaultValue) 
    a.pop(key) // 删除
    
>>> for key,value in a.items: //遍历dict
```

**set** 

set 与dict类似，也是一组key的集合，但是不存储value，由于key不能重复，所以set中不存在key

```  python
>>> s= set([1,1,2,3])
>>> {1,2,3}
>>> s.add(4) // 增
>>> {1,2,3,4}
>>> s.remove(4) //删
>>> {1,2,3}
>>> s1 = set([1,2,4])
>>> s1 & s2
>>> {1,2}
>>> s1 | s2
>>> {1,2,3,4}

```



### 再议不可变对象

字符串是不变对象，而list是可变对象

### 函数

默认参数

Python函数在定义的时候，默认参数L的值就被计算出来了，即[]，因为默认参数L也是一个变量，它指向对象[]，每次调用该函数，如果改变了L的内容，则下次调用时，默认参数的内容就变了，不再是函数定义时的[]了

 定义默认参数要牢记一点：默认参数必须指向不变对象！

``` python
def fn(name,gender,age=11,city='changsha'):
    print(f'name:{name}, gender: {gender},  age:{age},  city:{city}')

fn('name','F')
fn('name','F',11)
fn('name','F', city='xxxxx')

>>> def add_end(L=[]):
... 	L.append('end');
>>> add_end();
['end']
>>> add_end();
['end','end']

def add_end(L=None):
    if L is None:
        L = []
    L.append('END')
    return L

```

**可变参数**

``` python
 def calc(*numbers):
    sum = 0
    for n in numbers:
        sum = sum + n * n
    return sum
定义可变参数和定义一个list或tuple参数相比，仅仅在参数前面加了一个*号。在函数内部，参数numbers接收到的是一个tuple，因此，函数代码完全不变。但是，调用该函数时，可以传入任意个参数，包括0个参数,如果已经有一个list或者tuple，Python允许你在list或tuple前面加一个*号，把list或tuple的元素变成可变参数传进去
>>> nums = [1, 2, 3]
>>> calc(*nums)
14


```

**关键字参数**

可变参数允许你传入0个或任意个参数，这些可变参数在函数调用时自动组装为一个tuple。而关键字参数允许你传入0个或任意个含参数名的参数，这些关键字参数在函数内部自动组装为一个dict,可用来填充可选参数。

``` python
def person(x,y, **extra):
    print(f'x:{x},y:{y},extra:{extra}')
>>> person('x','y',z='z',f='f')
	x:x,y=y,extra:{'z':'z','f':'f'}
```

**命名关键字参数**

与关键字参数`**extra`不同，命名关键字参数需要一个特殊分隔符`*`，`*`后面的参数被视为命名关键字参数,传入参数时，必须传入参数名，否则将报错,如果函数定义中已经有了一个可变参数，后面跟着的命名关键字参数就不再需要一个特殊分隔符*了：

``` python
def person(name, age, *, city, job):
    print(name, age, city, job)
>>> person('Jack', 24, 'Beijing', 'Engineer')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: person() takes 2 positional arguments but 4 were given
 
def person(name, age, *args, city, job):
    print(name, age, args, city, job)
```



组合使用：

对于任意函数，都可以通过类似`func(*args, **kw)`的形式调用它，无论它的参数是如何定义的。

