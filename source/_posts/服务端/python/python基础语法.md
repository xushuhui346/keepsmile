---
title: python基础语法
date: 2019-08-08
categories: 
- 服务端
tags: 
- 服务端
- python
---

### 一、变量和简单数据类型
#### 1.字符串方法
- 字符串大小写：
.title()首字母大写
.upper()全部大写
.lower()全部小写
- 合并字符串
使用+号合并拼接字符串
- 使用制表符或换行符添加空白
\t  制表符
\n 换行符
- 删除空白
.rstrip() 删除末尾（右侧）空白
.lstrip() 删除开头（左侧）空白
.strip() 删除两端空白

#### 2.数字
- 使用函数str()避免类型错误
数字需要转为字符串才能和字符串拼接

#### 3.python之禅(命令行 import this)
- Beautiful is better than ugly.
(美胜于丑。)
- Simple is better than complex.
(简单胜于复杂。)
- Complex is better than complicated.
(复杂总比难懂好。)
- Readability counts.
(可读性计数。)
- There should be one-- and preferably only one --obvious way to do it.
(应该有一种——最好只有一种——显而易见的方法来做到这一点。)

### 二、列表简介
#### 1.列表是什么
就是js的数组，索引从0开始
#### 2.增删改元素
- .append()  末尾插入
- .insert(索引，值)  在列表指定位置添加新元素
- del  列表[索引]    删除元素（可以删除任一元素，但要知道索引）
- .pop()  删除列表最后一个元素，并将此元素返回
- .pop(0)  删除指定索引的元素，并将此元素返回
- .remove(元素值) 根据值删除元素  
注意： 方法remove() 只删除第一个指定的值。如果要删除的值可能在列表中出现多次，就需要使用循环来判断是否删除了所有这样的值。

#### 3.组织列表
- 使用.sort() 对列表进行永久性排序
- .sort(reverse=True) 倒序排序，也是永久性的
- .sorted() 对列表临时排序
- .reverse() 所有元素按相反顺序排列
- .len() 获取列表长度
- 每当需要访问最后一个列表元素时，都可使用索引-1 。这在任何情况下都行之有效，即便你最后一次访问列表后，其长度发生了变化。仅当列表为空时，这种访问最后一个元素的方式才会导致错误！

### 三、操作列表
#### 1.遍历整个列表
- for in :      (遍历的元素代码 需要缩进)

#### 2.避免缩进错误

#### 3.创建数值列表
- range()  打印一系列数字
range(1,4)  只会打印1,2,3  不包含4
- list(range(1,4)) ==>  [1,2,3]
- range() 还可以指定步长 list(range(2,11,2))   ==>  [2,4,6,8,10]
- 两个星号（**）表示乘方运算
- 对数字列表执行简单的统计计算
min(数字列表)  取最小值
max(数字列表)  取最大值
sum(数字列表)   求和
- 列表解析

#### 4.使用列表的一部分
- 切片    
list[0:3]  (索引，含前不含后)
list[:3] (从头开始)
list[2:] (到末尾)
list[-3:] (最后3个元素)
- 复制列表
list1 = list[:]  (首尾都没写，复制整个列表)
list1 = list (关联一个list，两个表改动，都会影响list)

#### 5.元组
- 不可变的列表称为元组
- 元组使用圆括号（），不适用方括号[]
- 直接改变元组中的元素是不可以的，会报错，如dimensions = (100,20)  dimensions[0]=50  (会报错)
- 修改元组的变量不会报错，是合法的，如dimensions = (100,20) 
dimensions = (400,20)  （合法，不报错）

#### 6.设置代码格式
- 每级缩进都使用四个空格。对你使用的文本编辑器进行设置，使其在你按Tab键时都插入四个空格。
- 每行都不要超过80字符。对你使用的编辑器进行设置，使其在第80个字符处显示一条垂直参考线。
- 不要在程序文件中过多地使用空行。

### 四、if语句
#### 1.条件测试
-  检查是否相等时不考虑大小写
在Python中检查是否相等时区分大小写，如果大小写很重要，这种行为有其优点。但如果大小写无关紧要，而只想检查变量的值，可将变量的值转换为小写，再进行比较。
```
>>> car = 'Audi'
>>> car.lower() == 'audi'
True
```
- 检查是否不相等
要检查是否两个人都不小于21岁，可使用下面的测试：
使用and 检查多个条件
```
>>> age_0 = 22
>>> age_1 = 18 
>>> age_0 >= 21 and age_1 >= 21
False 
>>> age_1 = 22
>>> age_0 >= 21 and age_1 >= 21
True
```
- 关键字or 也能够让你检查多个条件，但只要至少有一个条件满足，就能通过整个测试。仅当两个测试都没有通过时，使用or 的表达式才为False
-  要判断特定的值是否已包含在列表中，可使用关键字in 。
- 确定特定的值未包含在列表中很重要；在这种情况下，可使用关键字not in 。

#### 2.if语句
- if语句
```
age = 19
if age >= 18:
   print("You are old enough to vote!")
   print("Have you registered to vote yet?")
```
- if-else语句
```
age = 17 
 if age >= 18:
  print("You are old enough to vote!")
  print("Have you registered to vote yet?") 
else:
  print("Sorry, you are too young to vote.")
  print("Please register to vote as soon as you turn 18!")
```
- if-elif-else 结构
```
age = 12
if age < 4:
  print("Your admission cost is $0.") 
elif age < 18:
  print("Your admission cost is $5.") 
else:
  print("Your admission cost is $10.")
```
- 使用多个elif 代码块
- 省略else 代码块

#### 3.使用if语句处理列表
-  确定列表不是空的

### 五、字典
#### 1.一个简单的字典
```
alien_0 = {'color': 'green', 'points': 5}
print(alien_0['color'])
print(alien_0['points'])
```

#### 2.使用字典  键值对 用花括号{}
- 先创建一个空字典，再添加键值对
```
alien_0 = {}
alien_0['color'] = 'green'
alien_0['points'] = 5
print(alien_0)
```
- 修改字典中的值
```
alien_0 = {'color': 'green'}
print("The alien is " + alien_0['color'] + ".")
alien_0['color'] = 'yellow'
print("The alien is now " + alien_0['color'] + ".")
```
- 删除键值对（del）删除的键值对永远消失
```
alien_0 = {'color': 'green', 'points': 5}
print(alien_0)
del alien_0['points']
print(alien_0)
```

#### 3.遍历字典
- 遍历所有的键值对
```
for name, language in favorite_languages.items():
```
- 遍历所有的键
```
for name in favorite_languages.keys()：
```
遍历字典时，会默认遍历所有的键，因此，如果将上述代码中的for name in favorite_languages.keys(): 替换为for name in favorite_languages: ，输出将不变。
如果显式地使用方法keys() 可让代码更容易理解，你可以选择这样做，但如果你愿意，也可省略它。
-  按顺序遍历字典中的所有键
可使用函数sorted() 来获得按特定顺序排列的键列表的副本：
```
favorite_languages = {
    'jen': 'python',
    'sarah': 'c',
    'edward': 'ruby',
    'phil': 'python',
    }
for name in sorted(favorite_languages.keys()):
    print(name.title() + ", thank you for taking the poll.")
```
-  遍历字典中的所有值使用方法values()
```
for language in favorite_languages.values():
```
- 为剔除重复项，可使用集合（set）。集合 类似于列表，但每个元素都必须是独一无二的
```
favorite_languages = {
    'jen': 'python',
    'sarah': 'c',
    'edward': 'ruby',
    'phil': 'python',
    }
print("The following languages have been mentioned:") 
for language in set(favorite_languages.values()):
    print(language.title())
```

#### 4.嵌套
有时候，需要将一系列字典存储在列表将演示的，嵌套是一项强大的功能。
- 字典列表
```
alien_0 = {'color': 'green', 'points': 5}
alien_1 = {'color': 'yellow', 'points': 10}
alien_2 = {'color': 'red', 'points': 15}
aliens = [alien_0, alien_1, alien_2]
for alien in aliens:
    print(alien)
```
- 在字典中存储列表
```
pizza = {
    'crust': 'thick',
    'toppings': ['mushrooms', 'extra cheese'],
    }
```
- 在字典中存储字典
可在字典中嵌套字典，但这样做时，代码可能很快复杂起来。

### 六、用户输入和while循环
#### 1.使用int() 来获取数值输入
```
>>> age = input("How old are you? ")
How old are you? 21 
>>> age = int(age)
>>> age >= 18
True
```

#### 2.求模运算符（%取余）
```
number = input("Enter a number, and I'll tell you if it's even or odd: ")
number = int(number)
if number % 2 == 0:
    print("\nThe number " + str(number) + " is even.")
else:
    print("\nThe number " + str(number) + " is odd.")
```

#### 3.while循环
- while循环
```
prompt = "\nTell me something, and I will repeat it back to you:"
prompt += "\nEnter 'quit' to end the program. "
message = ""
while message != 'quit':
    message = input(prompt)
    if message != 'quit':
      print(message)
```
- 使用标志（变量）
在要求很多条件都满足才继续运行的程序中，可定义一个变量，用于判断整个程序是否处于活动状态。这个变量被称为标志 ，充当了程序的交通信号灯。你可让程序在标志为True 时继续运行，并在任何事件导致标志的值为False 时让程序停止运行。这样，在while 语句中就只需检查一个条件——标志的当前值是否为True ，并将所有测试（是否发生了应将标志设置为False 的事件）都放在其他地方，从而让程序变得更为整洁。
- 使用break 退出循环
要立即退出while 循环，不再运行循环中余下的代码，也不管条件测试的结果如何，可使用break 语句。
- 在循环中使用continue
要返回到循环开头，并根据条件测试结果决定是否继续执行循环，可使用continue 语句，它不像break 语句那样不再执行余下的代码并退出整个循环。
```
current_number = 0
while current_number < 10: 
    current_number += 1
    if current_number % 2 == 0:
        continue
    print(current_number)
```
结果： 1 3 5 7 9
- 使用while 循环来处理列表和字典
pop() 以每次一个的方式从列表unconfirmed_users 末尾删除
remove() 来删除列表中的特定值

### 七、函数
#### 1.定义函数
- 定义函数
```
def greet_user(): 
     """显示简单的问候语""" 
    print("Hello!")
greet_user()
```

#### 2. 实参和形参
```
def greet_user(username):
    """显示简单的问候语"""
    print("Hello, " + username.title() + "!")
greet_user('jesse')
```
在函数greet_user() 的定义中，变量username 是一个形参 ——函数完成其工作所需的一项信息。在代码greet_user('jesse') 中，值'jesse' 是一个实参 。实参是
调用函数时传递给函数的信息。
- 位置实参
最简单的关联方式是基于实参的顺序。这种关联方式被称为位置实参 。
- 关键字实参
关键字实参 是传递给函数的名称—值对。你直接在实参中将名称和值关联起来了，因此向函数传递实参时不会混淆（不会得到名为Hamster的harry这样的结果）。关键字实参让你无需考虑函数调用中的实参顺序，还清楚地指出了函数调用中各个值的用途。
```
def describe_pet(animal_type, pet_name):
    """显示宠物的信息"""
    print("\nI have a " + animal_type + ".")
    print("My " + animal_type + "'s name is " + pet_name.title() + ".")
describe_pet(animal_type='hamster', pet_name='harry')
describe_pet(pet_name='harry', animal_type='hamster')
```
上面最后两行代码，位置颠倒没关系，因为已经用关键字定义了参数。
- 默认值
```
def describe_pet(pet_name, animal_type='dog'):
    """显示宠物的信息"""
    print("\nI have a " + animal_type + ".")
    print("My " + animal_type + "'s name is " + pet_name.title() + ".")
describe_pet(pet_name='willie')
```
输出结果：
```
I have a dog.
My dog's name is Willie.
```

#### 3.返回值（return）
函数并非总是直接显示输出，相反，它可以处理一些数据，并返回一个或一组值。函数返回的值被称为返回值 。在函数中，可使用return 语句将值返回到调用函数的代码行。返回值让你能够将程序的大部分繁重工作移到函数中去完成，从而简化主程序。
- 让实参变成可选的
并非所有的人都有中间名，但如果你调用这个函数时只提供了名和姓，它将不能正确地运行。为让中间名变成可选的，可给实参middle_name 指定一个默认值——空字符串，并在用户没有提供中间名时不使用这个实参。为让get_formatted_name() 在没有提供中间名时依然可行，可给实参middle_name 指定一个默认值——空字符串，并将其移到形参列表的末尾：
```
def get_formatted_name(first_name, last_name, middle_name=''):
```
- 返回字典
函数可返回任何类型的值，包括列表和字典等较复杂的数据结构。
```
def build_person(first_name, last_name):
    """返回一个字典，其中包含有关一个人的信息"""
    person = {'first': first_name, 'last': last_name}
    return person
musician = build_person('jimi', 'hendrix') 
print(musician)
```
返回结果：
```
{'first': 'jimi', 'last': 'hendrix'}
```
- 禁止函数修改列表
有时候，需要禁止函数修改列表。为解决这个问题，可向函数传递列表的副本而不是原件；这样函数所做的任何修改都只影响副本，而丝毫不影响原件。
```
function_name(list_name[:])
```
切片表示法[:] 创建列表的副本。
- 传递任意数量的实参
有时候，你预先不知道函数需要接受多少个实参，好在Python允许函数从调用语句中收集任意数量的实参。
```
def make_pizza(*toppings):
    """打印顾客点的所有配料"""
    print(toppings)
make_pizza('pepperoni')
make_pizza('mushrooms', 'green peppers', 'extra cheese')
```
形参名*toppings 中的星号让Python创建一个名为toppings 的空元组，并将收到的所有值都封装到这个元组中。函数体内的print 语句通过生成输出来证明Python能够处理使用一个值调用函数的情形，也能处理使用三个值来调用函数的情形。它以类似的方式处理不同的调用，注意，Python将实参封装到一个元组中， **即便函数只收到一个值也如此**：
```
('pepperoni',)
('mushrooms', 'green peppers', 'extra cheese')
```
-  结合使用位置实参和任意数量实参
如果要让函数接受不同类型的实参，必须在函数定义中将接纳任意数量实参的形参放在最后。**Python先匹配位置实参和关键字实参，再将余下的实参都收集到最后一个形参中**。例如，如果前面的函数还需要一个表示比萨尺寸的实参，必须将该形参放在形参*toppings 的前面：
```
def make_pizza(size, *toppings):
    """概述要制作的比萨"""
    print("\nMaking a " + str(size) +
        "-inch pizza with the following toppings:")
    for topping in toppings:
        print("- " + topping)
make_pizza(16, 'pepperoni')
make_pizza(12, 'mushrooms', 'green peppers', 'extra cheese')
```

#### 4.将函数存储在模块中
- 导入整个模块
只需编写一条import 语句并在其中指定模块名，就可在程序中使用该模块中的所有函数。如果你使用这种import 语句导入了名为module_name.py 的整个模块，就可使用下面的语法来使用其中任何一个函数：
```
module_name.function_name()
```
- 导入特定的函数
你还可以导入模块中的特定函数，这种导入方法的语法如下：
```
from module_name import function_name
```
通过用逗号分隔函数名，可根据需要从模块中导入任意数量的函数：
```
from module_name import function_0, function_1, function_2
```
- 使用as 给函数指定别名
如果要导入的函数的名称可能与程序中现有的名称冲突，或者函数的名称太长，可指定简短而独一无二的别名 ——函数的另一个名称，类似于外号。要给函数指定这种特殊外号，需要在导入它时这样做。
```
from pizza import make_pizza as mp
mp(16, 'pepperoni')
mp(12, 'mushrooms', 'green peppers', 'extra cheese')
```
- 使用as 给模块指定别名
你还可以给模块指定别名。通过给模块指定简短的别名（如给模块pizza 指定别名p ），让你能够更轻松地调用模块中的函数。相比于pizza.make_pizza() ，p.make_pizza() 更为简洁：
```
import pizza as p
p.make_pizza(16, 'pepperoni')
p.make_pizza(12, 'mushrooms', 'green peppers', 'extra cheese')
```
- 导入模块中的所有函数
使用星号（* ）运算符可让Python导入模块中的所有函数：
```
from pizza import *
make_pizza(16, 'pepperoni')
make_pizza(12, 'mushrooms', 'green peppers', 'extra cheese')
```
import 语句中的星号让Python将模块pizza 中的每个函数都复制到这个程序文件中。由于导入了每个函数，可通过名称来调用每个函数，而无需使用句点表示法。  **然而，使用并非自己编写的大型模块时，最好不要采用这种导入方法**：如果模块中有函数的名称与你的项目中使用的名称相同，可能导致意想不到的结果：**Python可能遇到多个名称相同的函数或变量，进而覆盖函数，而不是分别导入所有的函数**。
最佳的做法是，要么只导入你需要使用的函数，要么导入整个模块并使用句点表示法。这能让代码更清晰，更容易阅读和理解。这里之所以介绍这种导入方法，只是想让你在阅读别人编写的代码时，如果遇到类似于下面的import 语句，能够理解它们：
```
from module_name import *
```

- 函数编写指南
(1)编写函数时，需要牢记几个细节。应给函数指定描述性名称，且**只在其中使用小写字母和下划线**。描述性名称可帮助你和别人明白代码想要做什么。给模块命名时也应遵循上述约定。
(2)每个函数都应包含简要地阐述其功能的注释，该注释应紧跟在函数定义后面，并采用文档字符串格式。文档良好的函数让其他程序员只需阅读文档字符串中的描述就能够使用它：他们完全可以相信代码如描述的那样运行；只要知道函数的名称、需要的实参以及返回值的类型，就能在自己的程序中使用它。
(3)给形参指定默认值时，等号两边不要有空格，对于函数调用中的关键字实参，也应遵循这种约定。
(4)PEP 8（https://www.python.org/dev/peps/pep-0008/ ）建议代码行的长度不要超过79字符，这样只要编辑器窗口适中，就能看到整行代码。如果形参很多，导致函数定义的长度超过了79字符，可在函数定义中输入左括号后按回车键，并在下一行按两次Tab键，从而将形参列表和只缩进一层的函数体区分开来。大多数编辑器都会自动对齐后续参数列表行，使其缩进程度与你给第一个参数列表行指定的缩进程度相同：
```
def function_name(
        parameter_0, parameter_1, parameter_2,
        parameter_3, parameter_4, parameter_5):
    function body...
```
(5)如果程序或模块包含多个函数，可使用两个空行将相邻的函数分开，这样将更容易知道前一个函数在什么地方结束，下一个函数从什么地方开始。
(6)所有的import 语句都应放在文件开头，唯一例外的情形是，在文件开头使用了注释来描述整个程序。

### 八、类
#### 1.创建和使用类
- 根据Dog 类创建的每个实例都将存储名字和年龄。我们赋予了每条小狗蹲下（sit() ）和打滚（roll_over() ）的能力：
```
class Dog(): 
    """一次模拟小狗的简单尝试"""
    def __init__(self, name, age):
        """初始化属性name和age"""
        self.name = name
        self.age = age
    def sit(self):
        """模拟小狗被命令时蹲下"""
        print(self.name.title() + " is now sitting.")
    def roll_over(self):
        """模拟小狗被命令时打滚"""
        print(self.name.title() + " rolled over!")
```
__init__() 是一个特殊的方法，每当你根据Dog 类创建新实例时，Python都会自动运行它。在这个方法的名称中，开头和末尾各有两个下划线，这是一种约定，旨在避免Python默认方法与普通方法发生名称冲突。
形参self 必不可少，还必须位于其他形参的前面。
```
lass Dog():
        --snip--
my_dog = Dog('willie', 6)
print("My dog's name is " + my_dog.name.title() + ".") 
print("My dog is " + str(my_dog.age) + " years old.")
```
上面实例化了对象，可以直接用句号（.）去调用相关的属性和方法。

#### 2.修改属性的值
- 1.直接修改属性的值
```
class Car():
     --snip--
my_new_car = Car('audi', 'a4', 2016)
print(my_new_car.get_descriptive_name())
my_new_car.odometer_reading = 23
my_new_car.read_odometer()
```
- 2.通过方法修改属性的值
```
class Car():
     --snip--
    def update_odometer(self, mileage):
        """将里程表读数设置为指定的值"""
        self.odometer_reading = mileage
my_new_car = Car('audi', 'a4', 2016)
print(my_new_car.get_descriptive_name())
my_new_car.update_odometer(23)
my_new_car.read_odometer()
```
- 3.通过方法对属性的值进行递增
```
class Car():
    --snip--
    def update_odometer(self, mileage):
        --snip--
    def increment_odometer(self, miles):
        """将里程表读数增加指定的量"""
        self.odometer_reading += miles
```

#### 3.继承
编写类时，并非总是要从空白开始。如果你要编写的类是另一个现成类的特殊版本，可使用继承 。一个类继承 另一个类时，它将自动获得另一个类的所有属性和方法；原有的类称为父类 ，而新类称为子类 。子类继承了其父类的所有属性和方法，同时还可以定义自己的属性和方法。
父类为Car:
```
class Car():
    """一次模拟汽车的简单尝试"""
    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0
    def get_descriptive_name(self):
        long_name = str(self.year) + ' ' + self.make + ' ' + self.model
        return long_name.title()
    def read_odometer(self):
        print("This car has " + str(self.odometer_reading) + " miles on it.")
    def update_odometer(self, mileage):
        if mileage >= self.odometer_reading:
            self.odometer_reading = mileage
        else:
            print("You can't roll back an odometer!")
    def increment_odometer(self, miles):
        self.odometer_reading += miles
```
子类ElectricCar继承父类Car:
```
class ElectricCar(Car):
    """电动汽车的独特之处"""
    def __init__(self, make, model, year):
        """初始化父类的属性"""
        super().__init__(make, model, year)
my_tesla = ElectricCar('tesla', 'model s', 2016)
print(my_tesla.get_descriptive_name())
```

- Python 2.7中的继承
```
class ElectricCar(Car):
    def __init__(self, make, model, year):
        super(ElectricCar, self).__init__(make, model, year)
        --snip--
```
函数super() 需要两个实参：子类名和对象self 。为帮助Python将父类和子类关联起来，这些实参必不可少。另外，在Python 2.7中使用继承时，务必在定义父类时在括号内指定object 。
- 重写父类方法
对于父类的方法，只要它不符合子类模拟的实物的行为，都可对其进行重写。为此，可在子类中定义一个这样的方法，即它与要重写的父类方法同名。这样，Python将不会考虑这个父类方法，而只关注你在子类中定义的相应方法。
假设Car 类有一个名为fill_gas_tank() 的方法，它对全电动汽车来说毫无意义，因此你可能想重写它。下面演示了一种重写方式：
```
def ElectricCar(Car):
    --snip--
    def fill_gas_tank():
        """电动汽车没有油箱"""
        print("This car doesn't need a gas tank!")
```
- 将实例用作属性
使用代码模拟实物时，你可能会发现自己给类添加的细节越来越多：属性和方法清单以及文件都越来越长。在这种情况下，可能需要将类的一部分作为一个独立的类提取出来。你可以将大型类拆分成多个协同工作的小类。
例如，不断给ElectricCar 类添加细节时，我们可能会发现其中包含很多专门针对汽车电瓶的属性和方法。在这种情况下，我们可将这些属性和方法提取出来，放到另一个名为Battery 的类中，并将一个Battery 实例用作ElectricCar 类的一个属性：
```
class Car():
--snip--
class Battery():
    """一次模拟电动汽车电瓶的简单尝试"""
    def __init__(self, battery_size=70):
        """初始化电瓶的属性"""
        self.battery_size = battery_size
    def describe_battery(self):
        """打印一条描述电瓶容量的消息"""
        print("This car has a " + str(self.battery_size) + "-kWh battery.")
class ElectricCar(Car):
    """电动汽车的独特之处"""
    def __init__(self, make, model, year):
        """ 初始化父类的属性，再初始化电动汽车特有的属性
"""
        super().__init__(make, model, year) 
        self.battery = Battery()
my_tesla = ElectricCar('tesla', 'model s', 2016)
print(my_tesla.get_descriptive_name())
my_tesla.battery.describe_battery()
```

#### 4.导入类
随着你不断地给类添加功能，文件可能变得很长，即便你妥善地使用了继承亦如此。为遵循Python的总体理念，应让文件尽可能整洁。为在这方面提供帮助，Python允许你将类存储在模块中，然后在主程序中导入所需的模块。
- 导入单个类
```
from car import Car
my_new_car = Car('audi', 'a4', 2016)
print(my_new_car.get_descriptive_name())
my_new_car.odometer_reading = 23
my_new_car.read_odometer()
```
的import 语句让Python打开模块car ，并导入其中的Car 类。这样我们就可以使用Car 类了，就像它是在这个文件中定义的一样。
- 在一个模块中存储多个类
虽然同一个模块中的类之间应存在某种相关性，但可根据需要在一个模块中存储任意数量的类。
- 从一个模块中导入多个类
```
from car import Car, ElectricCar
```
从一个模块中导入多个类时，用逗号分隔了各个类。导入必要的类后，就可根据需要创建每个类的任意数量的实例。
- 导入整个模块
你还可以导入整个模块，再使用句点表示法访问需要的类。这种导入方法很简单，代码也易于阅读。由于创建类实例的代码都包含模块名，因此不会与当前文件使用的任何名称发生冲突。
```
import car
```
- 导入模块中所有的类（不推荐用）
```
from module_name import *
```
- 在一个模块中导入另一个模块
有时候，需要将类分散到多个模块中，以免模块太大，或在同一个模块中存储不相关的类。将类存储在多个模块中时，你可能会发现一个模块中的类依赖于另一个模块中的类。在这种情况下，可在前一个模块中导入必要的类。

#### 5.python标准库
Python标准库 是一组模块，安装的Python都包含它。你现在对类的工作原理已有大致的了解，可以开始使用其他程序员编写好的模块了。可使用标准库中的任何函数和类，为此只需在程序开头包含一条简单的import 语句。
#### 6.类编码风格
- 类名应采用驼峰命名法 ，即将类名中的每个单词的首字母都大写，而不使用下划线。实例名和模块名都采用小写格式，并在单词之间加上下划线。
- 对于每个类，都应紧跟在类定义后面包含一个文档字符串。这种文档字符串简要地描述类的功能，并遵循编写函数的文档字符串时采用的格式约定。每个模块也都应包含一个文档字符串，对其中的类可用于做什么进行描述。
- 可使用空行来组织代码，但不要滥用。在类中，可使用一个空行来分隔方法；而在模块中，可使用两个空行来分隔类。
- 需要同时导入标准库中的模块和你编写的模块时，先编写导入标准库模块的import 语句，再添加一个空行，然后编写导入你自己编写的模块的import 语句。在包含多条import 语句的程序中，这种做法让人更容易明白程序使用的各个模块都来自何方。

### 九、文件和异常
#### 1.从文件中读取数据
- 读取整个文件
```
with open('pi_digits.txt') as file_object:
    contents = file_object.read()
    print(contents)
```
- 文件路径（相对路径）
linux、mac用  / ;windows用 \(反斜杠)
- 逐行读取 
要以每次一行的方式检查文件，可对文件对象使用for 循环：
```
filename = 'pi_digits.txt'
with open(filename) as file_object: 
    for line in file_object:
        print(line)
```
- 创建一个包含文件各行内容的列表
使用关键字with 时，open() 返回的文件对象只在with 代码块内可用。如果要在with 代码块外访问文件的内容，可在with 代码块内将文件的各行存储在一个列表中，并
在with 代码块外使用该列表：你可以立即处理文件的各个部分，也可推迟到程序后面再处理。
```
filename = 'pi_digits.txt'
with open(filename) as file_object:
    lines = file_object.readlines()
for line in lines:
    print(line.rstrip())
```
方法readlines() 从文件中读取每一行，并将其存储在一个列表中
- 使用文件的内容
读取文本文件时，Python将其中的所有文本都解读为字符串。如果你读取的是数字，并要将其作为数值使用，就必须使用函数int() 将其转换为整数，或使用
函数float() 将其转换为浮点数。
- 包含一百万位的大型文件

#### 2.写入文件
保存数据的最简单的方式之一是将其写入到文件中。通过将输出写入文件，即便关闭包含程序输出的终端窗口，这些输出也依然存在：你可以在程序结束运行后查看这些输出，可与别人分享输出文件，还可编写程序来将这些输出读取到内存中并进行处理。
- 写入文件
要将文本写入文件，你在调用open() 时需要提供另一个实参，告诉Python你要写入打开的文件。为明白其中的工作原理，我们来将一条简单的消息存储到文件中，而不是将其打印到屏幕上：
```
filename = 'programming.txt'
with open(filename, 'w') as file_object:
    file_object.write("I love programming.")
```
在这个示例中，调用open() 时提供了两个实参。第一个实参也是要打开的文件的名称；第二个实参（'w' ）告诉Python，我们要以写入模式 打开这个文件。打开文件
时，可指定**读取模式 （'r' ）、写入模式 （'w' ）、附加模式 （'a' ）或让你能够读取和写入文件的模式（'r+' ）**。如果你省略了模式实参，Python将以默认的只读模式打
开文件。
如果你要写入的文件不存在，函数open() 将自动创建它。然而，**以写入（'w' ）模式打开文件时千万要小心，因为如果指定的文件已经存在，Python将在返回文件对象前清空该文件。**
注意 **Python只能将字符串写入文本文件。要将数值数据存储到文本文件中，必须先使用函数str() 将其转换为字符串格式。**
- 写入多行
```
filename = 'programming.txt'
with open(filename, 'w') as file_object:
    file_object.write("I love programming.\n")
    file_object.write("I love creating new games.\n")
```
- 附加到文件
如果你要给文件添加内容，而不是覆盖原有的内容，可以附加模式 打开文件。你以附加模式打开文件时，Python不会在返回文件对象前清空文件，而你写入到文件的行都将添加到文件末尾。如果指定的文件不存在，Python将为你创建一个空文件。
```
filename = 'programming.txt'
with open(filename, 'a') as file_object:
    file_object.write("I also love finding meaning in large datasets.\n")
    file_object.write("I love creating apps that can run in a browser.\n")
```

#### 3.异常
Python使用被称为异常 的特殊对象来管理程序执行期间发生的错误。每当发生让Python不知所措的错误时，它都会创建一个异常对象。如果你编写了处理该异常的代码，程序将继续运行；如果你未对异常进行处理，程序将停止，并显示一个traceback，其中包含有关异常的报告。
异常是使用try-except 代码块处理的。try-except 代码块让Python执行指定的操作，同时告诉Python发生异常时怎么办。使用了try-except 代码块时，即便出现异常，
程序也将继续运行：显示你编写的友好的错误消息，而不是令用户迷惑的traceback。
- 处理ZeroDivisionError 异常（除以0引起的异常）
- 使用个try-except处理异常
当你认为可能发生了错误时，可编写一个try-except 代码块来处理可能引发的异常。你让Python尝试运行一些代码，并告诉它如果这些代码引发了指定的异常，该怎么办。处理ZeroDivisionError 异常的try-except 代码块类似于下面这样：
```
try:
    print(5/0)
except ZeroDivisionError:
    print("You can't divide by zero!")
```
- 使用异常避免崩溃
发生错误时，如果程序还有工作没有完成，妥善地处理错误就尤其重要。这种情况经常会出现在要求用户提供输入的程序中；如果程序能够妥善地处理无效输入，就能再提示用户提供有效输入，而不至于崩溃。
- else代码块
依赖于try 代码块成功执行的代码都应放到else 代码块中：
```
print("Give me two numbers, and I'll divide them.")
print("Enter 'q' to quit.")
while True:
    first_number = input("\nFirst number: ")
    if first_number == 'q':
        break
    second_number = input("Second number: ")
    try:
        answer = int(first_number) / int(second_number)
    except ZeroDivisionError:
        print("You can't divide by 0!") 
    else:
        print(answer)
```
try-except-else 代码块的工作原理大致如下：Python尝试执行try 代码块中的代码；只有可能引发异常的代码才需要放在try 语句中。有时候，有一些仅在try 代码块成功
执行时才需要运行的代码；这些代码应放在else 代码块中。except 代码块告诉Python，如果它尝试运行try 代码块中的代码时引发了指定的异常，该怎么办。
- 处理FileNotFoundError 异常
使用文件时，一种常见的问题是找不到文件：你要查找的文件可能在其他地方、文件名可能不正确或者这个文件根本就不存在。对于所有这些情形，都可使用try-except 代码块以直观的方式进行处理。
```
filename = 'alice.txt'
try:
    with open(filename) as f_obj:
        contents = f_obj.read()
except FileNotFoundError:
    msg = "Sorry, the file " + filename + " does not exist."
    print(msg)
```
- 分析文本
尝试计算它包含多少个单词。我们将使用方法split() ，它根据一个字符串创建一个单词列表。
方法split() 以空格为分隔符将字符串分拆成多个部分，并将这些部分都存储到一个列表中。结果是一个包含字符串中所有单词的列表，虽然有些单词可能包含标点。
- 使用多个文件
- 失败时一声不吭
在前一个示例中，我们告诉用户有一个文件找不到。但并非每次捕获到异常时都需要告诉用户，有时候你希望程序在发生异常时一声不吭，就像什么都没有发生一样继续运行。要让程序在失败时一声不吭，可像通常那样编写try 代码块，但在except 代码块中明确地告诉Python什么都不要做。Python有一个pass 语句，可在代码块中使用它来让Python 什么都不要做：
- 决定报告哪些错误
编写得很好且经过详尽测试的代码不容易出现内部错误，如语法或逻辑错误，但只要程序依赖于外部因素，如用户输入、存在指定的文件、有网络链接，就有可能出现异常。凭借经验可判断该在程序的什么地方包含异常处理块，以及出现错误时该向用户提供多少相关的信息。

#### 4.存储数据
很多程序都要求用户输入某种信息，如让用户存储游戏首选项或提供要可视化的数据。不管专注的是什么，程序都把用户提供的信息存储在列表和字典等数据结构中。用户关闭程序时，你几乎总是要保存他们提供的信息；一种简单的方式是使用模块json 来存储数据。
模块json 让你能够将简单的Python数据结构转储到文件中，并在程序再次运行时加载该文件中的数据。你还可以使用json 在Python程序之间分享数据。更重要的是，JSON数据格式并非Python专用的，这让你能够将以JSON格式存储的数据与使用其他编程语言的人分享。这是一种轻便格式，很有用，也易于学习。
- 使用json.dump() 和json.load()
```
import json
numbers = [2, 3, 5, 7, 11, 13]
filename = 'numbers.json'
with open(filename, 'w') as f_obj: 
    json.dump(numbers, f_obj)
```
```
import json
filename = 'numbers.json' 
with open(filename) as f_obj:
    numbers = json.load(f_obj)
print(numbers)
```
- 保存和读取用户生成的数据
```
import json
username = input("What is your name? ")
filename = 'username.json'
with open(filename, 'w') as f_obj: 
    json.dump(username, f_obj) 
    print("We'll remember you when you come back, " + username + "!")
```
- 重构
你经常会遇到这样的情况：代码能够正确地运行，但可做进一步的改进——将代码划分为一系列完成具体工作的函数。这样的过程被称为重构 。重构让代码更清晰、更易于理解、更容易扩展。

### 十、测试代码
#### 1.测试函数
- 单元测试和测试用例
Python标准库中的模块unittest 提供了代码测试工具。单元测试 用于核实函数的某个方面没有问题；测试用例 是一组单元测试，这些单元测试一起核实函数在各种情形下的行为都符合要求。良好的测试用例考虑到了函数可能收到的各种输入，包含针对所有这些情形的测试。全覆盖式测试用例包含一整套单元测试，涵盖了各种可能的函数使用方式。对于大型项目，要实现全覆盖可能很难。通常，最初只要针对代码的重要行为编写测试即可，等项目被广泛使用时再考虑全覆盖。
- 可通过的测试
创建测试用例的语法需要一段时间才能习惯，但测试用例创建后，再添加针对函数的单元测试就很简单了。要为函数编写测试用例，可先导入模块unittest 以及要测试的函数，再创建一个继承unittest.TestCase 的类，并编写一系列方法对函数行为的不同方面进行测试。
```
import unittest
from name_function import get_formatted_name
class NamesTestCase(unittest.TestCase):
    """测试name_function.py"""
    def test_first_last_name(self):
        """能够正确地处理像Janis Joplin这样的姓名吗？""" 
        formatted_name = get_formatted_name('janis', 'joplin') 
        self.assertEqual(formatted_name, 'Janis Joplin')
 unittest.main()
```
我们使用了unittest 类最有用的功能之一：一个断言 方法。断言方法用来核实得到的结果是否与期望的结果一致。在这里，我们知道get_formatted_name() 应
返回这样的姓名，即名和姓的首字母为大写，且它们之间有一个空格，因此我们期望formatted_name 的值为Janis Joplin 。为检查是否确实如此，我们调用unittest 的方法assertEqual() ，并向它传递formatted_name 和'Janis Joplin' 。代码行self.assertEqual(formatted_name, 'Janis Joplin') 的意思是说：“将formatted_name 的值同字符串'Janis Joplin' 进行比较，如果它们相等，就万事大吉，如果它们不相等，跟我说一声！”代码行unittest.main() 让Python运行这个文件中的测试。
```
.
----------------------------------------------------------------------
Ran 1 test in 0.000s
OK
```
第1行的句点表明有一个测试通过了。接下来的一行指出Python运行了一个测试，消耗的时间不到0.001秒。最后的OK 表明该测试用例中的所有单元测试都通过了。
- 不能通过的测试
- 测试未通过怎么办？
测试未通过时怎么办呢？如果你检查的条件没错，测试通过了意味着函数的行为是对的，而测试未通过意味着你编写的新代码有错。因此，测试未通过时，不要修改测试，而应修复导致测试不能通过的代码：检查刚对函数所做的修改，找出导致函数行为不符合预期的修改。
- 添加新测试
方法名必须以test_打头，这样它才会在我们运行test_name_function.py时自动运行。这个方法名清楚地指出了它测试的是get_formatted_name() 的哪个行为，这样，如果该测试未通过，我们就会马上知道受影响的是哪种类型的姓名。在TestCase 类中使用很长的方法名是可以的；这些方法的名称必须是描述性的，这才能让你明白测试未通过时的输出；这些方法由Python自动调用，你根本不用编写调用它们的代码。
#### 2.测试类
- 各种断言方法
6个常用的断言方法。使用这些方法可核实返回的值等于或不等于预期的值、返回的值为True 或False 、返回的值在列表中或不在列表中。你只能在继承unittest.TestCase 的类中使用这些方法，下面来看看如何在测试类时使用其中的一个。
![](a.png)
- 方法setUp()
如果你在TestCase 类中包含了方法setUp() ，Python将先运行它，再运行各个以test_打头的方法。这样，在你编写的每个测试方法中都可使用在方法setUp() 中创建的对象了。
