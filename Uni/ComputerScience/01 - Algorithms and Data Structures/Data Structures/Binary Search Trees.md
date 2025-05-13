A binary tree is a finite set of nodes which are either empty or consist of a root and two disjoint binary trees, a left subtree and a right subtree. There is one entry point known as the root which is parentless, and each node has at most two children. Childless nodes are called leaves.

Every node (excluding the root) is connected by a directed edge from exactly one other node. In other words a node can have only one parent. Right and left child nodes are different.

BST's are useful since they allow for fast inset, lookup and delete operations (if done properly).

To insert - Traverse the existing tree according to fixed rules, insert new element in appropriate place.
To lookup - Traverse tree according to fixed rules.
To delete - First do a lookup, and if found, delete the node and fix tree structure if necessary.

The crucial property of BST's which allows for such efficient is that the left child (and all descending elements) of any node is smaller, and the right child (and all descending elements) is always larger.

For all operations (searching, insertion, deletion) the time complexity is O(h) where h is the height of the tree, but this degenerates to O(n) in the worst case, where all nodes go in direction. This can be avoided using balanced trees like [[Balanced Trees|AVL trees]] or Red-Black trees.
## Array representation of BST
One advantage of an array based implementation is the ability to represent the position p with a single integer. However, space usage of an array based representation depends on the shape of the tree. Some update operations for the tree cannot be efficiently supported. For example, deleting a node and promoting its child takes O(n) time because it is not just the child that moves locations within the array but all descendants of the child.

# Tree Traversals
A traversal is an operation which consists of visiting each node exactly once. Most traversals are naturally recursive.

## Preorder traversal
In preorder traversal the root is visited first. A preorder traversal can be described as follows:
```
function preorder(node):
	if x exists:
		print x.data
		preorder(node.left)
		preorder(node.right)
```

## In order traversal
In in order, the root node is visited in the middle.
```
function preorder(node):
	if x exists:
		preorder(node.left)
		print x.data
		preorder(node.right)
```
The in order traversal gives the elements in sorted order.
## Postorder traversal
In post order, the root node is visited last.
```
function preorder(node):
	if x exists:
		preorder(node.left)
		preorder(node.right)
		print x.data
```

# Deleting from a BST
- If the element being deleted has no children you can just delete it.
- If the element has one child (left or right), delete it and replace it with the child node, and move the child's sub-tree up.
- If the element has two child nodes, replace the deleted node with the node found by going one step to the right and as far to the left as possible after that.
