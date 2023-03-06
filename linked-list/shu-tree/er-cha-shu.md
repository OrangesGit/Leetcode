# 二叉树

### 什么是二叉搜索树？

一个树被称为二叉树，如果它满足每一个节点都有0～2个字节点。

## 代码实现

```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right
```

## 二叉树遍历

最基本的是三种遍历方式，中、前、后序遍历

### 中序遍历
