title: Python相关知识点

top: true

categories: 

- 面试

tags:

- python

description: <center><h3>python相关知识点</h3></center>

---

<!--more-->

### 1.Python中深拷贝和浅拷贝和赋值的区别

1. copy.copy 浅拷贝 只拷贝父对象，不会拷贝对象内部的子对象。
2. copy.deepcopy 深拷贝 拷贝对象及其子对象
    一个很好的例子：
    import copy
    a = [1, 2, 3, 4, ['a', 'b']] #原始对象
    b = a #赋值，传对象的引用
    c = copy.copy(a) #对象拷贝，浅拷贝
    d = copy.deepcopy(a) #对象拷贝，深拷贝
    a.append(5) #修改对象a
    a[4].append('c') #修改对象a中的['a', 'b']数组对象
    print 'a = ', a
    print 'b = ', b
    print 'c = ', c
    print 'd = ', d
    输出结果：
    a = [1, 2, 3, 4, ['a', 'b', 'c'], 5]
    b = [1, 2, 3, 4, ['a', 'b', 'c'], 5]
    c = [1, 2, 3, 4, ['a', 'b', 'c']]
    d = [1, 2, 3, 4, ['a', 'b']]

### 2. Python垃圾回收

**Python中的垃圾回收是以引用计数为主，标记-清除和分代收集为辅。引用计数最大缺陷就是循环引用的问题，所以Python采用了辅助方法。**