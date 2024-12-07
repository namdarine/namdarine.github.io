---
layout: post

title: Binary Search Tree (BST)

date: 2022-02-17 20:00:00

description: Concepts and understanding of Binary Search Tree (BST)

tags: WIL

categories: JAVA Data_Structure

toc:
  sidebar: left
---

# Tree

Tree is a **nonlinear** structure in which each node is capable of having many successor nodes, called _children_. Trees are <U>useful for representing lots of varied relationships among data items</U>.

## Definitions

- **Tree**: A structure with a unique starting node (root), in which each node is capable of having multiple successor nodes (its children), and in which a unique path exists from the root to every other node.
- **Root**: The top node of a tree structure; a node with no parent.
- **Parent node**: The predecessor node of a node is its parent.
- **Subtree**: A node and all of its descendants form a subtree rooted at the node.
<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/BST/BST_structure.png" class="img-fluid rounded z-depth-1" %}
</div>
</div>

## Require

A tree's subtrees must be disjoint. There is a unique path from the root of a tree to any other node of the tree. Every child has only one parent.

<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/BST/BST_require.jpeg" class="img-fluid rounded z-depth-1" %}
</div>
</div>

## More Definitions

- **Ancestor**: A parent of a node, or a parent of an ancestor.
- **Descendant**: A child of a node, or a child of a descendant.
- **Leaf**: A node that has no children.
- **Interior node**: A node that is not a leaf.
- **Siblings**: Nodes with the same parent.
- **Level**: The level of a node is its distance from the root (the number of connections between itself and the root).
- **Height**: The maximum level of the tree.

### Example

<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/BST/BST_example.jpeg" class="img-fluid rounded z-depth-1" %}
</div>
</div>

- The <U>ancestors</U> of P are H, X and A.
- The <U>descendant</U> of X are H, Q, Z and P.
- The <U>leaf nodes</U> are C, T, F, P, Q and Z.
- The <U>interior nodes</U> are A, B, and X.
- The <U>siblings</U> of B are F and X.

<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/BST/BST_level.jpeg" class="img-fluid rounded z-depth-1" %}
</div>
</div>

- The <U>height</U> of this tree is 3.

## Traversal

### Breadth-First Traversal

Also called "level-order traversal"
Using Queue

<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/BST/BST_breadth.jpeg" class="img-fluid rounded z-depth-1" %}
</div>
</div>

### Depth-First Traversal

Using Stack

<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/BST/BST_depth.jpeg" class="img-fluid rounded z-depth-1" %}
</div>
</div>

# Binary Search Trees

- **Binary Tree**: A tree in which each node is capable of having **two child nodes**, a left child node and a right child node.

A binary tree in which the key value in any node.

- is **greater than or equal to** the key value in **its left child** and any of its descendants (the nodes in the left subtree).
- is **less than** the key value in **its right child** and any of its descendants (the nodes in the right subtree).

## Feature

1. Each node contains a distinct data value.
2. The key values in the tree can be compared using "greater than" and "less than".
3. The key value of each node in the tree is less than every key value in its right subtree, and greater than every key value in its left subtree.

## Traversals

<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/BST/BST_traversal.jpeg" class="img-fluid rounded z-depth-1" %}
</div>
</div>

### Preorder traversal

1. Root
2. Left subtree
3. Right subtree
   P → F → B → H → G → S → R → Y → T → W → Z

```java
public void preorder() {
    preorder(root);
}

private void preorder(BSTNode<T> node) {
    if (node != null) {
        System.out.print(node.getKey());    // Root
        preorder(node.getLeft());           // Left subtree
        preorder(node.getRight());          // Rigth subtree
    }
}
```

### Inorder traversal

1. Left subtree
2. Root
3. Right subtree
   B → F → G → H → P → R → S → T → W → Y → Z

```java
public void inorder() {
    inorder(root);
}

private void inorder(BSTNode<T> node) {
    if (node != null) {
        inorder(node.getLeft());                // Left subtree
        System.out.print(node.getKey() + " ");  // Root
        inorder(node.getRight());               // Right subtree
    }
}
```

### Postorder traversal

1. Left subtree
2. Right subtree
3. Root
   B → G → H → F → R → W → T → Z → Y → S → P

```java
public void postorder() {
    postorder(root);
}

private void postorder(BSTNode<T> node) {
    if (node != null) {
        postorder(node.getLeft());              // Left subtree
        postorder(node.getRight());             // Right subtree
        System.out.print(node.getKey() + " ");  // Root
    }
}
```

## Implementation

### BST Node

```java
public class BSTNode<T> {
    private T key;
    private T data;
    private BSTNode<T> left;
    private BSTNode<T> right;

    // Constructor
    public BSTNode(T key) {
        this.key = key;
        this.data = data;
        left = null;
        right = null;
    }

    // Setter
    public void setKey (T key) {
        this.key = key;
    }

    public void setData (T data) {
        this.data = data;
    }

    public void setLeft (BSTNode<T> link) {
        left = link;
    }

    public void setRight (BSTNode<T> link) {
        right = link;
    }

    // Getter
    public T getKey() {
        return key;
    }

    public T getData() {
        return data;
    }

    public BSTNode<T> getLeft() {
        return left;
    }

    public BSTNode<T> getRight() {
        return right;
    }

    void print() {
        System.out.println(data);
    }
}
```

### Constructors

```java
import java.util.*;

public class BST<T> {
    private BSTNode<T> root;
    private Comparator <? super T> comparator = null;

    // Constructor
    public BST() {
        root = null;
    }

    public BST(Comparator<? super T> c) {
        this();
        coparator = c;
    }
}
```

### Observers

```java
// Observers
// Calculate size of the tree with recursive method
public int recSize() {
    return recSize(root);
}

public int recSize(BSTNode<T> node) {
    if (node == null)
        return 0;

    else
        return 1 + recSize(node.getLeft()) + recSize(node.getRight());
}

// Calculate size of the tree with iterative method
public int itersize() throws StackOverflowException, stackUnderflowException {
    int count = 0;
    if (root != null) {
        ArrayStack<BSTNode<T>> nodeStack = new ArrayStack<BSTNode<T>>();
        BSTNOde<T> currNode;
        nodeStack.push(root);
        while (!nodeStack.isEmpty()) {
            currNode = nodeStack.top();
            nodeStack.pop();
            count++;

            if(currNode.getLeft() != null)
                nodeStack.push(currNode.getLeft());

            if(currNode.getRight() != null)
                nodeStack.push(currNode.getRight());
        }
    }

    return count;
}

// Find Maximum depth of the tree
public int maxDepth() {
    return findDepth(root, 0);
}

public int findDepth(BSTNode<T> node, int depth) {
    if (node == null)
        return depth;

    return Math.max(findDepth(node.getLeft(), depth + 1), findDeptho(node.getRight(), depth + 1));
}

public boolean isEmpty() {
    return (root = null);
}

// Get smallest element in this BST
public T min() {
    if (isEmpty())  // If this BST is empty, returns null.
        return null;

    else {
        BSTNode<T> node = root;
        while (node.getLeft() != null)
            node = node.getLeft();

        return node.getKey();
    }
}

// Get largest element in this BST
public T max() {
    if (isEmpty())  // If this BST is empty, returns null.
        return null;

    else {
        BSTNode<T> node = root;
        while (node.getRight() != null)
            node = node.getRight();

        return node.getKey();
    }
}
```

### Transformers

#### Add

A new node is always inserted into its appropriate position in the tree as a leaf.
If a new node is smaller than a root node, add the new node on the left of the root node. If it is greater than the root node, add it on the right of the root node.

<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/BST/BST_add.jpeg" class="img-fluid rounded z-depth-1" %}
</div>
</div>

```java
// Transformers
// Add Node T to subtree
private void addNode (BSTNode<T> node, T key) {
    int cond = compa(key, node.getKey());
    if (cond == 0)
        return;

    else if (cond < 0) {
        if (node.getLeft() == null)
            node.setLeft(new BSTNode<T>(key));

        else
            addNode(node.getLeft(), key);
    }

    else {
        if (node.getRight() == null)
            node.setRight(new BSTNode<T>(key));

        else
            addNode(node.getRight(), key);
    }
}

// Add Node
public void add(T key) {
    if (root == null)
        root = new BSTNode<T>(key);

    else
        addNode(root, key);
}
```

#### Remove

Must ensure when remove an element maintain the binary search tree property.

- **Removing a leaf**
  Removing a leaf is simply a matter of setting the <U>appropriate link of its parent to null</U>.

<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/BST/BST_romove_leaf.jpeg" class="img-fluid rounded z-depth-1" %}
</div>
</div>

- **Removing a node with only one child**
  Make the reference from the parent <U>skip over the removed node and point instead to the child of the node we intend to remove</U>.

<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/BST/BST_remove_child.jpeg" class="img-fluid rounded z-depth-1" %}
</div>
</div>

- **Removing a node with two children**
  Replaces the node's info with the info from another node in the tree so that the search property is retained - then remove this other node.

<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/BST/BST_remove_children.jpeg" class="img-fluid rounded z-depth-1" %}
</div>
</div>

```java
// Remove node
public boolean remove (T target) {
    root = remove(target, root);
    return found;
}

private BSTNode<T> remove (T target, BSTNode<T> node) {
    if (node == null)
        found = false;

    else if (compa(target, node.getKey()) < 0)
        node.setLeft(remove(target, node.getLeft()));

    else if (compa(target, node.getKey()) > 0)
        node.setRight((remove(target, node.getRight())));

    else {
        node = removeNode(node);
        found = true;
    }

    return node;
}

private BSTNode<T> removeNode (BSTNode<T> node) {
    T data;
    if (node.getLeft() == null)
        return node.getRight();

    else if (node.getRight() == null)
        return node.getLeft();

    else {
        data = getPredecessor(node.getLeft());
        node.setKey(data);
        node.setLeft(remove(data, node.getLeft()));
        return node;
    }
}
```

## Performance

- A Binary search tree is an appropriate structure for many of the same applications discussed previously in conjunction with sorted lists.
- There is a space cost - the binary search tree, with its <U>extra reference in each node, takes up more memory space than a singly linked list</U>.
- Similar to a sorted array-based list, it can be searched quickly, using a binary search.
- Similar to a linked list, it allows insertions and removals without having to move large amounts of data.

## Big-O

Compare BST to Linear LIsts

<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/BST/BST_bigO.jpeg" class="img-fluid rounded z-depth-1" %}
</div>
</div>

## Binary Tree and its Array Representation

<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/BST/BST_array.jpeg" class="img-fluid rounded z-depth-1" %}
</div>
</div>

To implement the algorithms that manipulate the tree, must be able to find the left and right child of a node in the tree.

- tree.nodes[index] left child is in tree.nodes[index * 2 + 1].
- tree.nodes[index] right child is in tree.nodes[index * 2 + 2].

Also, can determine the location of its parent node

- tree.nodes[index]'s parent is in tree.nodes[(index - 1) / 2].

If the tree is complete, this representation works best, space wise.

## Full Binary Tree

A binary tree in which all of the leaves are on the same level and every non-leaf node has two children.

<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/BST/BST_full.png" class="img-fluid rounded z-depth-1" %}
</div>
</div>

## Complete Binary Tree

A binary tree that is either full or full through the next-to-last level, with the leaves on the last level as far to the left as possible.

<div class="row mt-3">
<div class="col-sm mt-3 mt-md-0">
{% include figure.liquid loading="eager" path="assets/img/BST/BST_complete.png" class="img-fluid rounded z-depth-1" %}
</div>
</div>

The complete binary tree with 'k' height has maximum $$2^{k+1} - 1$$ nodes.
In the other words, the complete binary tree which saves 'n' nodes has log(n) height.

## Reference

- _CS401-Data Structure_. (2021). Micheal Y. Choi, Ph.D. Illinois Institute of Technology.
- _Full Binary Tree_. (2019). Image. Retrieved February 15, 2022, from <a href="https://soldonii.tistory.com/75">soldonii</a>.
- _Complete Binary Tree_. (2018). Image. Retrieved February 15, 2022, from <a href="https://medium.com/jiwon-bae/data-structure-binary-tree-f6fe881b0554">medium.com/jiwon-bae</a>.

> https://github.com/namdarine/DataStructure.git <br>
> Full code is in "BST" package in this repository.
