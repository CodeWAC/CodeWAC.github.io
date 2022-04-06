# python技巧记录

[toc]

## 基本语法

- 语法
- 条件判断
- 循环

语法，空格决定逻辑层次关系，行末尾无分号;。

若单行太长，当不在一个括号中时，使用`\`续接下一行。



条件判断`if else`

![image-20200517223310085](D:\Repository\MyBlogs\Gitbook\杂记\python技巧记录.assets\image-20200517223310085.png)



循环`for`和`while`

![image-20200517223542923](D:\Repository\MyBlogs\Gitbook\杂记\python技巧记录.assets\image-20200517223542923.png)

1. 注意`for`循环之后，`i`并没有被销毁。
2. `for`可以和`else`搭配。当`for`循环中没有`break`跳出，则执行完`for`之后会执行`else`中代码。



![image-20200517223757453](D:\Repository\MyBlogs\Gitbook\杂记\python技巧记录.assets\image-20200517223757453.png)



## 常用数据结构

1. `list`
2. `dict`
3. `set`
4. `collections.deque()`
5. `collections.defaultdict()`
6. `collections.Counter()`

### list

#### 列表加法、乘法。

![image-20200517224509987](D:\Repository\MyBlogs\Gitbook\杂记\python技巧记录.assets\image-20200517224509987.png)

**乘法要注意列表中存储的数据类型是否是可变类型**，如果是可变类型，列表乘法相当于复制该对象的引用，若改变其中一个，其余都会受到影响。

![image-20200517225132993](D:\Repository\MyBlogs\Gitbook\杂记\python技巧记录.assets\image-20200517225132993.png)

观察，b和a都是存储了列表`[1, 2]`的引用，所以改变一个，其他的都会改变。



#### 内置常用方法

- 索引
- `list.append()`和`list.pop()`
- `list.extend()`
- `list.sort()`和`sorted(list)`

索引支持负数从列表尾为-1，依次往前-2， -3……

切片`list[left:right:step]`，包含左端点，不包含右端点，每隔step取一个，构成一个新列表。



`list.append()`和`list.pop()`都是类似栈，对栈尾添加和删除元素。`append()`无返回值，`pop()`返回退出列表的元素。

因为python中`list`数据结构内部实现类似数组，所以`list.remove(), list.pop(0)`，都要移动后面的元素，时间复杂度为 $O(n)$ 较高，用的少。



`list1.extend(list2)`用于合并两个数组，将`list2`合并至`list1`，改变了`list1`，无返回值。

![image-20200517230305194](D:\Repository\MyBlogs\Gitbook\杂记\python技巧记录.assets\image-20200517230305194.png)



`list.sort()`对列表进行排序，是**稳定**的，会改变列表，无返回值。

可通过设置`key`来决定排序参考基准，下例是使用数组长度来排序，通常使用方法`key = lambda x: ...`

![image-20200517230741180](D:\Repository\MyBlogs\Gitbook\杂记\python技巧记录.assets\image-20200517230741180.png)

`sorted(list)`和`list.sort()`基本一样，但`sorted(list)`不会改变待排序列表，而是返回一个已排好序的副本列表。

![image-20200517231339952](D:\Repository\MyBlogs\Gitbook\杂记\python技巧记录.assets\image-20200517231339952.png)





#### 构建多维列表

例如二维：`[[0]*n for _ in range(m)]`m行n列。