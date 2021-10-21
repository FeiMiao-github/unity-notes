# Lua

* 轻量级
* 可扩展
* 面向过程和函数式编程
* 自动内存管理
* 语言内置模式匹配;闭包;函数也可以看作一个值;提供多线程支持

## 全局变量

在默认情况下，变量总是认为是全局变量

## 数据类型


|数据类型|描述|
| :--- | ---- |
| `nil` | `nil`表示一个无效值。作为条件判断时,等价于`false` |
| `boolean` |`true`或`false`|
| `number` |双精度实浮点数|
| `string` |由单引号或双引号来表示|
| `function` |由lua或C编写的函数|
| `userdata` |表示任意存储在变量中的C数据结构|
| `thread` |表示执行的独立线路，用于执行协同程序|
| `table` |Lua 中的表（table）其实是一个"关联数组"（associative arrays），数组的索引可以是数字、字符串或表类型。在 Lua 里，table 的创建是通过"构造表达式"来完成，最简单构造表达式是{}，用来创建一个空表。|

### boolean

在 Lua 语言中，条件测试（例如控制结构中的分支语句）将除 Boolean 值 false 和 nil 外的所有其他值视为真 。
**<font color=red>特别的是，在条件检测中 Lua 语言把零和空字符串也都视为真 。</font>**

```
local line = "============"

function Test(val)
    if (val) then
        print(val, line, "true")
    end
end

Test(0) -------------> 0       ============    true
Test("")------------->         ============    true
```



### 字符串

使用`[[]]`表示一块字符串

 ```lua
 html = [[
 <html>
 <head></head>
 <body>
     <a href="http://www.runoob.com/">菜鸟教程</a>
 </body>
 </html>
 ]]
 print(html)
 ```

使用 # 来计算字符串的长度，放在字符串前面

```lua
len = "www.runoob.com"
print(#len) -- 14
```

### table

在 Lua 里，table 的创建是通过"构造表达式"来完成，最简s单构造表达式是{}，用来创建一个空表。也可以在表里添加一些数据，直接初始化表

**Lua 中的表（table）其实是一个"关联数组"（associative arrays），数组的索引可以是数字或者是字符串。**

**table 不会固定长度大小，有新数据添加时 table 长度会自动增长，没初始的 table 都是 nil。**

### thread

在 Lua 里，最主要的线程是协同程序（coroutine）

线程跟协程的区别：**线程可以同时多个运行，而协程任意时刻只能运行一个，并且处于运行状态的协程只有被挂起（suspend）时才会暂停。**

### userdata

userdata 是一种用户自定义数据，用于表示一种由应用程序或 C/C++ 语言库所创建的类型，可以将任意 C/C++ 的任意数据类型的数据（通常是 struct 和 指针）存储到 Lua 变量中调用。

## Lua 变量

Lua 变量有三种类型：全局变量、局部变量、表中的域。

Lua 中的变量全是全局变量，哪怕是语句块或是函数里，除非用 local 显式声明为局部变量。

## Lua 循环

### while 循环

```lua
while(condition)
do
   statements
end
```

```lua
a=10
while( a < 20 )
do
   print("a 的值为:", a)
   a = a+1
end
```

###  for 循环

#### 数值for循环

```lua
-- [[var 从 exp1 变化到 exp2，每次变化以 exp3 为步长递增 var，并执行一次 **"执行体"**。exp3 是可选的，如果不指定，默认为1。]]--
for var=exp1,exp2,exp3 do  
    <执行体>  
end  
```

#### 泛型for循环

```lua
a = {"one", "two", "three"}
for i, v in ipairs(a) do
    print(i, v)
end 
```

### Repeat循环

```lua
--[ 变量定义 --]
a = 10
--[ 执行循环 --]
repeat
   print("a的值为:", a)
   a = a + 1
until( a > 15 )
```

### break 语句

Lua 编程语言 break 语句插入在循环体中，用于退出当前循环或语句，并开始脚本执行紧接着的语句

### goto语句

```lua
local a = 1
::label:: print("--- goto label ---")

a = a+1
if a < 3 then
    goto label   -- a 小于 3 的时候跳转到标签 label
end
```

## Lua 流程控制

### if...elseif...else 语句

```lua
if( 布尔表达式 1)
then
   --[ 在布尔表达式 1 为 true 时执行该语句块 --]

elseif( 布尔表达式 2)
then
   --[ 在布尔表达式 2 为 true 时执行该语句块 --]

elseif( 布尔表达式 3)
then
   --[ 在布尔表达式 3 为 true 时执行该语句块 --]
else 
   --[ 如果以上布尔表达式都不为 true 则执行该语句块 --]
end
```

##  函数

- 1.完成指定的任务，这种情况下函数作为调用语句使用；
- 2.计算并返回值，这种情况下函数作为赋值语句的表达式使用。

### 函数定义

```lua
optional_function_scope function function_name( argument1, argument2, argument3..., argumentn)
    function_body
    return result_params_comma_separated
end
```

**optional_function_scope:** 该参数是可选的制定函数是全局函数还是局部函数，未设置该参数默认为全局函数，如果你需要设置函数为局部函数需要使用关键字 **local**

## Lua 字符串

- 单引号间的一串字符。
- 双引号间的一串字符。
- **[[** 与 **]]** 间的一串字符。

## Lua 迭代器

### 泛型 for 迭代器

```lua
array = {"Google", "Runoob"}

for key,value in ipairs(array)
do
   print(key, value)
end
```

### 无状态的迭代器

无状态的迭代器是指不保留任何状态的迭代器，因此在循环中我们可以利用无状态迭代器避免创建闭包花费额外的代价。

```lua
function square(iteratorMaxCount,currentNumber)
   if currentNumber<iteratorMaxCount
   then
      currentNumber = currentNumber+1
   return currentNumber, currentNumber*currentNumber
   end
end

for i,n in square,3,0
do
   print(i,n)
end
```

### 多状态的迭代器

很多情况下，迭代器需要保存多个状态信息而不是简单的状态常量和控制变量，最简单的方法是使用闭包，还有一种方法就是将所有的状态信息封装到 table 内，将 table 作为迭代器的状态常量，因为这种情况下可以将所有的信息存放在 table 内，所以迭代函数通常不需要第二个参数。

```lua
print("==============闭包================")
local function EIterator(array)
    -- 闭包状态
    local index = 0
    local count = #array

    return function ()
        index = index + 1
        if (index <= count)
        then
            return index, array[index]
        end
    end
end

local function PrintFor(array)
    for i, v in EIterator(array)
    do
        print(i, "----", v)
    end
end

Tab = {"a", "b", "c", "d"}
PrintFor(Tab)
```

## Lua table(表)

* Lua table 使用关联型数组，你可以用任意类型的值来作数组的索引，但这个值不能是 nil。

* Lua也是通过table来解决模块（module）、包（package）和对象（Object）的

### table(表)的构造

```lua
-- 初始化表
mytable = {}

-- 指定值
mytable[1]= "Lua"

-- 移除引用
mytable = nil
-- lua 垃圾回收会释放内存
```

## Lua 模块与包

### module创建

Lua 的模块是由变量、函数等已知元素组成的 table，因此创建一个模块很简单，就是创建一个 table，然后把需要导出的常量、函数放入其中，最后返回这个 table 就行。以下为创建自定义模块 module.lua，文件代码格式如下

```lua
-- 文件名为 module.lua
-- 定义一个名为 module 的模块
module = {}
 
-- 定义一个常量
module.constant = "这是一个常量"
 
-- 定义一个函数
function module.func1()
    io.write("这是一个公有函数！\n")
end
 
local function func2()
    print("这是一个私有函数！")
end
 
function module.func3()
    func2()
end
 
return module
```

### require 函数

```lua
require("<模块名>")
```

或

```lua
require "<模块名>"
```

## Lua 元表(Metatable)

有两个很重要的函数来处理元表：

- **setmetatable(table,metatable):** 对指定 table 设置元表(metatable)，如果元表(metatable)中存在 __metatable 键值，setmetatable 会失败。
- **getmetatable(table):** 返回对象的元表(metatable)。

### __index 元方法

### __newindex 元方法

### 为表添加操作符

| 模式     | 描述               |
| -------- | ------------------ |
| __add    | 对应的运算符 '+'.  |
| __sub    | 对应的运算符 '-'.  |
| __mul    | 对应的运算符 '*'.  |
| __div    | 对应的运算符 '/'.  |
| __mod    | 对应的运算符 '%'.  |
| __unm    | 对应的运算符 '-'.  |
| __concat | 对应的运算符 '..'. |
| __eq     | 对应的运算符 '=='. |
| __lt     | 对应的运算符 '<'.  |
| __le     | 对应的运算符 '<='. |

### __call 元方法

### __tostring 元方法

```lua
-- 添加__call
t = nil
other = nil

t = {1, 2, 3, 4}
setmetatable(t, {
    __call = function (tb)
        local sum = 0
        for i = 1, Len(tb) do
            sum = sum + tb[i]
        end
        return sum
    end,

    __tostring = function (tb)
        local str = "{"
        local len = Len(tb)

        for i = 1, len, 1 do
            str = str..tostring(tb[i])
            if (i ~= len) then
                str = str .. ","
            end
        end

        str = str .. "}"
        return str
    end
})

print(t())
print(t)
```

## Lua 协同程序(coroutine)

### 线程和协同程序区别

线程与协同程序的主要区别在于，一个具有多个线程的程序可以同时运行几个线程，而协同程序却需要彼此协作的运行。

在任一指定时刻只有一个协同程序在运行，并且这个正在运行的协同程序只有在明确的被要求挂起的时候才会被挂起。

协同程序有点类似同步的多线程，在等待同一个线程锁的几个线程有点类似协同。

### 基本语法

| 方法                  | 描述                                                         |
| --------------------- | ------------------------------------------------------------ |
| `coroutine.create()`  | 创建 coroutine，返回 coroutine， 参数是一个函数，当和 resume 配合使用的时候就唤醒函数调用 |
| `coroutine.resume()`  | 重启 coroutine，和 create 配合使用                           |
| `coroutine.yield()`   | 挂起 coroutine，将 coroutine 设置为挂起状态，这个和 resume 配合使用能有很多有用的效果 |
| `coroutine.status()`  | 查看 coroutine 的状态  注：coroutine 的状态有三种：dead，suspended，running，具体什么时候有这样的状态请参考下面的程序 |
| `coroutine.wrap（）`  | 创建 coroutine，返回一个函数，一旦你调用这个函数，就进入 coroutine，和 create 功能重复 |
| `coroutine.running()` | 返回正在跑的 coroutine，一个 coroutine 就是一个线程，当使用running的时候，就是返回一个 corouting 的线程号 |

## Lua 文件 I/O

- 简单模式（simple model）拥有一个当前输入文件和一个当前输出文件，并且提供针对这些文件相关的操作。
- 完全模式（complete model） 使用外部的文件句柄来实现。它以一种面对对象的形式，将所有的文件操作定义为文件句柄的方法

```lua
file = io.open (filename [, mode])
```

| 模式 | 描述                                                         |
| ---- | ------------------------------------------------------------ |
| r    | 以只读方式打开文件，该文件必须存在。                         |
| w    | 打开只写文件，若文件存在则文件长度清为0，即该文件内容会消失。若文件不存在则建立该文件。 |
| a    | 以附加的方式打开只写文件。若文件不存在，则会建立该文件，如果文件存在，写入的数据会被加到文件尾，即文件原先的内容会被保留。（EOF符保留） |
| r+   | 以可读写方式打开文件，该文件必须存在。                       |
| w+   | 打开可读写文件，若文件存在则文件长度清为零，即该文件内容会消失。若文件不存在则建立该文件。 |
| a+   | 与a类似，但此文件可读可写                                    |
| b    | 二进制模式，如果文件是二进制文件，可以加上b                  |
| +    | 号表示对文件既可以读也可以写                                 |

### 简单模式

简单模式使用标准的 I/O 或使用一个当前输入文件和一个当前输出文件。

| 模式         | 描述                                                         |
| ------------ | ------------------------------------------------------------ |
| "*n"         | 读取一个数字并返回它。例：file.read("*n")                    |
| "*a"         | 从当前位置读取整个文件。例：file.read("*a")                  |
| "*l"（默认） | 读取下一行，在文件尾 (EOF) 处返回 nil。例：file.read("*l")   |
| number       | 返回一个指定字符个数的字符串，或在 EOF 时返回 nil。例：file.read(5) |

### 完全模式

## Lua 错误处理

### 语法错误

### 运行错误

### 错误处理

#### error函数

#### assert函数

#### pcall 和 xpcall、debug

## Lua 调试(Debug)

## Lua 面向对象

