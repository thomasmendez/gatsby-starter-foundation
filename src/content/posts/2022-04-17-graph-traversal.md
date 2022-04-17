---
template: blog-post
title: Graph Traversal
slug: graph-traversal
date: 2022-04-17 13:43
description: Graphs
---
**Inorder Traversal:** Left, Root, Right

```
def inorder_traversal(self, root: Optional[Node], order: List[int]) -> None:
  if (node != None):
    self.inorder_traversal(self, root.left, order)
    order.append(root.val)
    self.inorder_traversal(self, root.right, order)
```

**Preorder Traversal:** Root, Left, Right

```
def preorder_traversal(self, root: Optional[Node], order: List[int]) -> None:
  if (node != None):
    order.append(root.val)
    self.preorder_traversal(self, root.left, order)
    self.preorder_traversal(self, root.right, order)
```

**Postorder Traversal:** Left, Right, Root



```
def postorder_traversal(self, root: Optional[Node], order: List[int]) -> None:
  if (node != None):
    self.postorder_traversal(self, root.left, order)
    self.postorder_traversal(self, root.right, order)
    order.append(root.val)
 
```