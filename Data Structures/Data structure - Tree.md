---
tags:
  - data_structure
---


# Tree - Cây

![[tree.png]]

## Là cấu trúc dữ liệu thể hiện dữ liệu phân cấp

## Key points - Điểm chính

- Tập hợp các đối tượng, thực thể (node) và liên kết với nhau để thể hiện hoặc mô phỏng một hệ thống phân cấp.
- Phi tuyến tính (ko lưu trữ data 1 cách tuần tự) và là một cấu trúc phân cấp (các phần tử được sắp xếp theo nhiều cấp độ).
- Node gốc ở trên cùng, mỗi node có thể chứa kiểu dữ liệu bất kì.
- Node con chứa dữ liệu và liên kết/tham chiếu từ node cha.

## Basic terms - Thuật ngữ cơ bản

- Root
- Child node - Nút con
- Parent - Nút cha
- Sibling - Anh chị em
- Leaf Node - Nút lá: node ngoài cùng, ko có node con nào.
- Internal nodes - Các nút bên trong: Có ít nhất một nút con.
- Ancestor node - Nút tổ tiên: Nút 1, 2, 5 là tổ tiên của nút 10.
- Descendant - Hậu duệ:  Nút 10 là hậu duệ của nút 5.

## Properties - Thuộc tính


## General Tree - Cây tổng hợp

- Không có bất kì cấu hình & giới hạn số lượng children.

```js
class TreeNode {
  constructor(data) {
    this.data = data;
    this.children = [];
  }

  addChild(childNode) {
    this.children.push(childNode);
  }
}

class GeneralTree {
  constructor(rootData) {
    this.root = new TreeNode(rootData);
  }
}

// Example usage:

// Creating a tree with 'A' as the root
const tree = new GeneralTree("A");

// Adding children to the root
const nodeB = new TreeNode("B");
const nodeC = new TreeNode("C");
const nodeD = new TreeNode("D");

tree.root.addChild(nodeB);
tree.root.addChild(nodeC);
tree.root.addChild(nodeD);

// Adding children to node B
const nodeB1 = new TreeNode("B1");
const nodeB2 = new TreeNode("B2");
nodeB.addChild(nodeB1);
nodeB.addChild(nodeB2);

// Adding children to node C
const nodeC1 = new TreeNode("C1");
nodeC.addChild(nodeC1);

// Adding children to node D
const nodeD1 = new TreeNode("D1");
const nodeD2 = new TreeNode("D2");
nodeD.addChild(nodeD1);
nodeD.addChild(nodeD2);
/*
GeneralTree {
  root: TreeNode {
    data: 'A',
    children: [ [TreeNode], [TreeNode], [TreeNode] ]
  }
}
*/

```

## Binary Tree - Cây nhị phân

![[binary-tree (1).png]]

- Tối đa 2 children ở mỗi node
- Ko có thứ tự sắp xếp các node
- Types: 
	- Full binary tree
	- Complete binary tree
	- Extended Binary tree and more
- Chia theo dạng phân cấp(level)
- Cho phép trùng values
- Tốc độ deletion, insertion, and searching chậm hơn do ko sắp xếp theo thứ tự
- Time complexity: O(n)

```js
class TreeNode {
  constructor(data) {
    this.data = data;
    this.left = null;
    this.right = null;
  }
}

// Binary Tree
const binaryTreeRoot = new TreeNode(1);
const nodeB = new TreeNode(2);
const nodeC = new TreeNode(3);
const nodeD = new TreeNode(4);
const nodeE = new TreeNode(5);

binaryTreeRoot.left = nodeB;
binaryTreeRoot.right = nodeC;
nodeB.left = nodeD;
nodeB.right = nodeE;

/*
  TreeNode {
  data: 1,
  left: TreeNode {
    data: 2,
    left: TreeNode { data: 4, left: null, right: null },
    right: TreeNode { data: 5, left: null, right: null }
  },
  right: TreeNode { data: 3, left: null, right: null }
}
/*
```



## Binary Search Tree - Cây tìm kiếm nhị phân

![[binary-tree.png]]

- Tối đa 2 children ở mỗi node
- Left children < Parent Node < Right children
- Types: 
	- AVL tree
	- Splay Tree
	- T-trees and more
- Phân chia theo thứ tự (Left node < Right node)
- Không cho phép values trùng lặp
- Tốc độ deletion, insertion, and searching nhanh do được sắp xếp theo thứ tự
- Time complexity: O(log n)

```js
class TreeNode {
  constructor(data) {
    this.data = data;
    this.left = null;
    this.right = null;
  }
}

class BinaryTree {
  constructor() {
    this.root = null;
  }

  insert(data) {
    const newNode = new TreeNode(data);

    if (this.root === null) {
      this.root = newNode;
    } else {
      this.insertNode(this.root, newNode);
    }
  }

  insertNode(node, newNode) {
    if (newNode.data < node.data) {
      if (node.left === null) {
        node.left = newNode;
      } else {
        this.insertNode(node.left, newNode);
      }
    } else {
      if (node.right === null) {
        node.right = newNode;
      } else {
        this.insertNode(node.right, newNode);
      }
    }
  }
}

// Example usage:

const binaryTree = new BinaryTree();

binaryTree.insert(10);
binaryTree.insert(5);
binaryTree.insert(15);
binaryTree.insert(3);
binaryTree.insert(7);
/*
  BinaryTree {
    root: TreeNode {
      data: 10,
      left: TreeNode { data: 5, left: [TreeNode], right: [TreeNode] },
      right: TreeNode { data: 15, left: null, right: null }
    }
  }
*/

```

## AVL Tree - Cây nhị phân đặc biệt

![[avl-tree.png]]

- Là Binary search tree tự cân bằng
- Chiều cao của 2 node con của bất cứ node nào khác nhau tối đa 1.
- Nếu khác nhau nhiều hơn 1, cơ chế tái cân bằng(rebalancing) được thực hiện để khôi phục thuộc tính này

```js
class TreeNode {
  constructor(data) {
    this.data = data;
    this.height = 1;
    this.left = null;
    this.right = null;
  }
}

class AVLTree {
  constructor() {
    this.root = null;
  }

  height(node) {
    return node ? node.height : 0;
  }

  updateHeight(node) {
    node.height = 1 + Math.max(this.height(node.left), this.height(node.right));
  }

  balanceFactor(node) {
    return node ? this.height(node.left) - this.height(node.right) : 0;
  }

  rotateRight(y) {
    const x = y.left;
    const T2 = x.right;

    x.right = y;
    y.left = T2;

    this.updateHeight(y);
    this.updateHeight(x);

    return x;
  }

  rotateLeft(x) {
    const y = x.right;
    const T2 = y.left;

    y.left = x;
    x.right = T2;

    this.updateHeight(x);
    this.updateHeight(y);

    return y;
  }

  insert(root, data) {
    if (!root) {
      return new TreeNode(data);
    }

    if (data < root.data) {
      root.left = this.insert(root.left, data);
    } else if (data > root.data) {
      root.right = this.insert(root.right, data);
    } else {
      // Duplicate values are not allowed in AVL trees.
      return root;
    }

    this.updateHeight(root);

    const balance = this.balanceFactor(root);

    // Left Left Case
    if (balance > 1 && data < root.left.data) {
      return this.rotateRight(root);
    }

    // Right Right Case
    if (balance < -1 && data > root.right.data) {
      return this.rotateLeft(root);
    }

    // Left Right Case
    if (balance > 1 && data > root.left.data) {
      root.left = this.rotateLeft(root.left);
      return this.rotateRight(root);
    }

    // Right Left Case
    if (balance < -1 && data < root.right.data) {
      root.right = this.rotateRight(root.right);
      return this.rotateLeft(root);
    }

    return root;
  }

  insertNode(data) {
    this.root = this.insert(this.root, data);
  }
}

// Example usage:

const avlTree = new AVLTree();

avlTree.insertNode(10);
avlTree.insertNode(5);
avlTree.insertNode(15);
avlTree.insertNode(3);
avlTree.insertNode(7);

/*
  TreeNode {
  data: 10,
  height: 3,
  left: TreeNode {
    data: 5,
    height: 2,
    left: TreeNode { data: 3, height: 1, left: null, right: null },
    right: TreeNode { data: 7, height: 1, left: null, right: null }
  },
  right: TreeNode { data: 15, height: 1, left: null, right: null }
}  
*/

```


## B Tree

-  Sử dụng rộng rãi để truy cập đĩa
- Lưu trữ số lượng lớn keys trong một node và các giá trị khóa lớn bằng cách giữ height của tree tương đối nhỏ

 ![[b-tree.png]]


```js
class BTreeNode {
  constructor(isLeaf = true) {
    this.keys = [];
    this.children = [];
    this.isLeaf = isLeaf;
  }
}

class BTree {
  constructor(order) {
    this.root = new BTreeNode();
    this.order = order;
  }

  insert(key) {
    const root = this.root;

    if (root.keys.length === 2 * this.order - 1) {
      const newRoot = new BTreeNode(false);
      newRoot.children.push(this.root);
      this.splitChild(newRoot, 0);
      this.root = newRoot;
      this.insertNonFull(newRoot, key);
    } else {
      this.insertNonFull(root, key);
    }
  }

  insertNonFull(x, key) {
    let i = x.keys.length - 1;

    if (x.isLeaf) {
      while (i >= 0 && key < x.keys[i]) {
        i--;
      }

      x.keys.splice(i + 1, 0, key);
    } else {
      while (i >= 0 && key < x.keys[i]) {
        i--;
      }

      i++;

      if (x.children[i].keys.length === 2 * this.order - 1) {
        this.splitChild(x, i);

        if (key > x.keys[i]) {
          i++;
        }
      }

      this.insertNonFull(x.children[i], key);
    }
  }

  splitChild(x, i) {
    const t = this.order;
    const y = x.children[i];
    const z = new BTreeNode(y.isLeaf);
    x.children.splice(i + 1, 0, z);
    x.keys.splice(i, 0, y.keys[t - 1]);

    z.keys = y.keys.splice(t, t - 1);

    if (!y.isLeaf) {
      z.children = y.children.splice(t, t);
    }
  }
}

// Example usage:

const bTree = new BTree(2);

bTree.insert(3);
bTree.insert(7);
bTree.insert(1);
bTree.insert(5);
bTree.insert(9);
bTree.insert(2);
bTree.insert(4);
bTree.insert(6);
bTree.insert(8);
bTree.insert(10);

/*
  BTreeNode {
    keys: [ 5 ],
    children: [
      BTreeNode { keys: [Array], children: [Array], isLeaf: false },
      BTreeNode { keys: [Array], children: [Array], isLeaf: false }
    ],
    isLeaf: false
  }
*/

```