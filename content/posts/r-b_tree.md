+++
draft = false
date = 2018-09-05T13:14:01+08:00
title = "R-B Tree"
slug = ""
tags = []
categories = []
+++

https://blog.csdn.net/v_JULY_v/article/details/6105630


### 性质

1. 每个结点要么是红的要么是黑的。  
2. 根结点是黑的。  
3. 每个叶结点（叶结点即指树尾端NIL指针或NULL结点）都是黑的。  
4. 如果一个结点是红的，那么它的两个儿子都是黑的。  
5. 对于任意结点而言，其到叶结点树尾端NIL指针的每条路径都包含相同数目的黑结点。 



### 插入

```
RB-INSERT(T, z)
y ← nil
x ← T.root
while x ≠ T.nil
    do y ← x
    if z.key < x.key
        then x ← x.left
    else x ← x.right
z.p ← y
if y == nil[T]
    then T.root ← z
else if z.key < y.key
    then y.left ← z
else y.right ← z
z.left ← T.nil
z.right ← T.nil
z.color ← RED
RB-INSERT-FIXUP(T, z)

```

RB-INSERT(T, z)前面的第1～13行代码基本上就是二叉查找树的插入代码，然后第14～16行代码把z的左孩子和右孩子都赋为叶结点nil，再把z结点着为红色，最后为保证红黑性质在插入操作后依然保持，调用一个辅助程序RB-INSERT-FIXUP来对结点进行重新着色，并旋转。

换言之，如果插入的是根结点，由于原树是空树，此情况只会违反性质2，因此直接把此结点涂为黑色；如果插入的结点的父结点是黑色，由于此不会违反性质2和性质4，红黑树没有被破坏，所以此时什么也不做。

```
RB-INSERT-FIXUP(T, z)
while z.p.color == RED
    do if z.p == z.p.p.left
        then y ← z.p.p.right
        if y.color == RED
            then z.p.color ← BLACK               # Case 1
            y.color ← BLACK                      # Case 1
            z.p.p.color ← RED                    # Case 1
            z ← z.p.p                            # Case 1
        else if z == z.p.right
            then z ← z.p                         # Case 2
            LEFT-ROTATE(T, z)                     # Case 2
        z.p.color ← BLACK                        # Case 3
        z.p.p.color ← RED                        # Case 3
        RIGHT-ROTATE(T, z.p.p)                    # Case 3
    else (same as then clause with "right" and "left" exchanged)
T.root.color ← BLACK
```

### 插入修复情况

1. 当前结点的父结点是红色，祖父结点的另一个子结点（叔叔结点）是红色。
2. 当前节点的父节点是红色,叔叔节点是黑色，当前节点是其父节点的右子
3. 当前节点的父节点是红色,叔叔节点是黑色，当前节点是其父节点的左孩子