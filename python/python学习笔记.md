
# python学习笔记

## 基础知识

- 脚本式编程
>通过脚本参数调用解释器开始执行脚本，直到脚本执行完毕。当脚本执行完成后，解释器不再有效。

```bash
#!/usr/bin/python
print "Hello, Python!"
```

- 标识符

>在 Python 里，标识符由字母、数字、下划线组成。
在 Python 中，所有标识符可以包括英文、数字以及下划线(_)，但不能以数字开头。
Python 中的标识符是区分大小写的。
以下划线开头的标识符是有特殊意义的。以单下划线开头 _foo 的代表不能直接访问的类属性，需通过类提供的接口进行访问，不能用 from xxx import * 而导入。
以双下划线开头的 __foo 代表类的私有成员，以双下划线开头和结尾的 __foo__ 代表 Python 里特殊方法专用的标识，如 __init__() 代表类的构造函数。

- 行和缩进

>学习 Python 与其他语言最大的区别就是，Python 的代码块不使用大括号 {} 来控制类，函数以及其他逻辑判断。python 最具特色的就是用缩进来写模块。
缩进的空白数量是可变的，但是所有代码块语句必须包含相同的缩进空白数量，这个必须严格执行。使用的缩进方式不一致，有的是 tab 键缩进，有的是空格缩进，改为一致即可。
在 Python 的代码块中必须使用相同数目的行首缩进空格数。
建议你在每个缩进层次使用 单个制表符 或 两个空格 或 四个空格 , 切记不能混用
多行语句
Python语句中一般以新行作为语句的结束符。
但是我们可以使用斜杠（ \）将一行的语句分为多行显示，如下所示：

```python
total = item_one + \
        item_two + \
        item_three
```

>语句中包含 [], {} 或 () 括号就不需要使用多行连接符。

- Python引号

>Python 可以使用引号( ' )、双引号( " )、三引号( ''' 或 """ ) 来表示字符串，引号的开始与结束必须的相同类型的。
其中三引号可以由多行组成，编写多行文本的快捷语法，常用于文档字符串，在文件的特定地点，被当做注释。
Python注释
python中单行注释采用 # 开头。
python 中多行注释使用三个单引号(''')或三个双引号(""")。

- Class, Object and Members

```
# A simple example class
class Test:
	# A sample method
	def fun(self):
		print("Hello")
# Driver code
obj = Test()
obj.fun()
```

>The self

>1. Class methods must have an extra first parameter in method definition. We do not give a value for this parameter when we call the method, Python provides it
>2. If we have a method which takes no arguments, then we still have to have one argument – the self. See fun() in above simple example.
>3. This is similar to this pointer in C++ and this reference in Java.

>>When we call a method of this object as myobject.method(arg1, arg2), this is automatically converted by Python into MyClass.method(myobject, arg1, arg2) – this is all the special self is about.
- \_\_init\_\_ method
> The __init__ method is similar to constructors in C++ and Java. It is run as soon as an object of a class is instantiated. The method is useful to do any initialization you want to do with your object.

```
# A Sample class with init method 
class Person: 
	# init method or constructor 
	def __init__(self, name): 
		self.name = name 

	# Sample Method 
	def say_hi(self): 
		print('Hello, my name is', self.name) 

p = Person('Shwetanshu') 
p.say_hi() 
```

- python函数的四种参数传递方式

>python中函数传递参数有四种形式

```python
fun1(a,b,c)
fun2(a=1,b=2,c=3)
fun3(*args)
fun4(**kargs)
```

>**第一种**```fun1(a,b,c)``是直接将实参赋予行参，根据位置做匹配，即严格要求实参的数量与行参的数量位置相等，比较一般，大多数语言常用这种方式。`

> **第二种** ```fun2(a=1,b=2,c=3)```根据键值对的形式做实参与行参的匹配，通过这种式就可以忽略了参数的位置关系，直接根据关键字来进行赋值，同时该种传参方式还有个好处就是可以在调用函数的时候作为个别选填项，不要求数量上的相等，即可以fun5(3,4)来调用fun2函数，这里关键就是前面的3,4覆盖了原来a、b两个行参的值，但c还是不变采用原来的默认值3，这种模式相较第一种更加灵活，不仅可以通过fun6(c=5,a=2,b=7)来打乱行参的位置，而且可以在但没有对应行参传递的时候常用定义函数时的默认值。

>**第三种**```fun3(*args)```这传参方式是可以传入任意个参数，这些若干参数都被放到了tuple元组中赋值给行参args，之后要在函数中使用这些行参，直接操作args这个tuple元组就可以了，这样的好处是在参数的数量上没有了限制，但是因为是tuple，其本身还是有次序的，这就仍然存在一定的束缚，在对参数操作上也会有一些不便

>**第四种**```fun4(**kargs)```最为灵活，其是以键值对字典的形式向函数传参，含有第二种位置的灵活的同时具有第三种方式的数量上的无限制。此外第三四种函数声明的方式前的’*’,与c里面的指针声明一样，这里仅做声明标识之用

>最后要强调的是四种传递方式混合使用(大多数情况是这种),fun7(a,b,*c,**d),但四种方式混用时要遵守：
>+ args = 须在args之后
>+ *args须在args=value之后
>+ **kargs须在*args之后

[Python 函数中，参数是传值，还是传引用？](https://foofish.net/python-function-args.html)