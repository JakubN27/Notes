If a [[Binary Search Trees|BST]] is balanced then the complexity of its operations is h = O(log n)
If a [[Binary Search Trees|BST]] is degenerated then h = Ω(n)

You can, however, take care that a BST does not degenerate when inserting or deleting, without excessive overhead work.

# Rotations
Rotations are standard re-balancing operations which keep a tree efficient. These are applied when a nodes left and right subtrees differ by more than one.

## Right Rotation
When the nodes right subtree is taller than its left subtree. This moves the right child up, making it the new parent.

## Left Rotation
When the nodes left subtree is smaller than its right subtree. This moves the left child up, making it the new parent.

## Right-Left Rotation
As the name says, a right rotation followed by a left rotation. this is used when the unbalanced node has a left child whose right tree is heavier. We can also say it is used when its child and grandchild are not on the same side.

## Left-Right Rotation
As the name says, a left rotation followed by a right rotation. this is used when the unbalanced node has a right child whose left tree is heavier. We can also say it is used when its child and grandchild are not on the same side.

# AVL Trees
An AVL tree is a self-balancing BST with the additional property of: For each node v, the heights of v's children differ by at most 1.
The height of an AVL tree storing n keys  is O(log n). Standard BST operations in AVL trees take O(log n) time. 

## Insertion
- Insertion into left subtree of left child of an unbalanced node requires a [[#Right Rotation]] to rebalance.
- Insertion into right subtree of right child of an unbalanced node requires a [[#Left Rotation]] to rebalance.
- Insertion into right subtree of left child of an unbalanced node requires a [[#Left-Right Rotation]] to rebalance.
- Insertion into left subtree of right child of an unbalanced node requires a [[#Right-Left Rotation]] to rebalance.
## Deletion
If p is the parent of the deleted node (which is not always the node that contained deleted data), there may be unbalanced nodes of the path from p to the root. We must keep going up the tree and rebalancing the tree where needed.

The post processing for insertion and deletion can be unified:
- Both trace an upward path from some node
- Both use trinode restructuring when an unbalanced node is found
We can stop post-processing when we reach an ancestor whose height didn't change or trinode restructuring of a subtree results in the same height as before insertion/deletion. 
To detect this, can store the old height of each node.