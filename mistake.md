# Mistake

## Python

### Function

1. 一般来说，函数要有返回值. NoneType error 通常是函数没有返回值导致的. 对于方法的返回值更要注意
2. 参数默认值只初始化一次！:construction:
3. f(x=1, y) 这肯定是错误的
4. 定义函数时，使用了 kw 型参数，却忘了在被调用函数中使用的 kw 型参数
5. 主函数调用函数时，参数设置不正确，不符合被调用函数语法（可能报出类型错误）



### Class

1. 定义方法的修饰符时，不要用obj.foo(), 而是 foo(obj)

2. 类的属性值没有=参数，而是设置了其他值

3. 父类继承顺序会影响方法的继承。方法优先继承第一个父类的方法，其他父类的方法不起作用。

   

### Grammar

1. while, 不是 While （注意颜色）

2. 字典的顺序是随机的。可以用OrderedDict固定顺序

3. 生成器只能生成一次

4. 循环/索引指标可能和其他变量冲突

5. 生成器不能用来做列表推导

6. {0:spec}.format(self) 调用` __format__(self, 'spec')`, {0} 时调用 `__format__(self, '')`, 不是 `__format__(self, None)` 或` __format__(self) `

   

### Coding

1. 如果要修改某个代码，记得修改重复出现的代码 :construction:
2. 记得把改过的代码改回来！
3. **粗心**，不可违背自己定义好的语法规则. *粗心可怕*
4. 构造等价程序要小心特殊情况！ 🚧
5. 拷贝了一个项目，在一个项目中修改了文件，却没有修改另一个，而我一直在调用没有修改的文件，总是出不来结果



### Encoding

1. 含有汉字的utf-8文件读取，用open(filename, encoding='utf-8')

   

### Package

1. 注意`__all__`, `from ... import *` 只能导入其中字符串对应的变量

2. 文件名不能与标准库和第三方库相同，会报出意外的错误，同样的代码在别的文件中能运行，在某个文件中不能。 🚧

*对包的载入机制还有盲点*

### standard libs

下述程序会多次执行`print('wtf')`

```python
print('wtf')
if __name__ == "__main__":

    from multiprocessing import Process, Manager

    manager = Manager()
    results = manager.dict()
    ...
    # start and join
```

### 3rd part libs

1. 优先于 |, 比如 c + (a|b) (pyparsing)
2. 正确使用 setParseAction/addParseAction (pyparsing)
3. 两个np.uint8(0~255)相加可能发生溢出错误
4. `A[0:2,0:2]=np.mat([[8,8],[2,2]])` 是正确的, `A[0:2,0:2]=[[8,8],[2,2]]` 会导致错误的结果
5. pandas 无法用to_pickle保存数据，是因为数据中包含一些非内置对象
