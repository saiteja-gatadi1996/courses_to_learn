## Binary Trees and Binary Search Trees
A binary tree is a linked data structure (Binary tree is a hierarchical data structure) where each node points to two child nodes (at most). The child nodes are called the left child and right child.

Here are the properties of a binary tree.

- Each node can point to two children at most.
- The top most element in the tree is called root.
- Two Children are usually referred as Left Child and Right Child.
- The nodes which don’t point to any children are called leaf nodes.
- Non-leaf nodes are called internal nodes. Root is also an internal node if it’s not a leaf node. Let’s step through a few visualizations to internalize these properties.
![image](https://user-images.githubusercontent.com/42731246/195991623-4db14b50-4ed8-4f41-8936-aec4c729277c.png)

##### Q) If a Tree has only 1 node, what type of node is it (select all that apply)?

###### Ans: A root node and A leaf node

-----

## Height and Depth of the Tree

- The Depth of the node is the number of nodes on the path from the root to the node. Root has depth 0.

- You can see that for depth, we begin counting from the root, down towards to the node, starting at 0. 


![image](https://user-images.githubusercontent.com/42731246/195992950-6f67f9db-fee1-4625-bf17-5b968c9f3729.png)

- The Height of the node is the number of nodes on the path from the node to the deepest leaf. All leaf nodes have height 0.

- For height, we start counting from the node, up towards the root, again starting at 0. Some people start counting depth and height from 1 instead of 0 and it's just a matter of preference.

- The Height of the tree is the maximum height of any node in the tree. 

![image](https://user-images.githubusercontent.com/42731246/195993010-8af127dd-3030-4803-94f1-dd44f38593ae.png)

## Key of the node and Subtree

- In many practical situations, a node contains several fields of data with a key

![image](https://user-images.githubusercontent.com/42731246/195993697-686ca595-2f55-4c8a-ac00-905b0e203e00.png)

![image](https://user-images.githubusercontent.com/42731246/195993885-617a12c7-128d-45b5-9e11-2b7879337121.png)

## Binary Search Tree (BST)
A binary tree is a BST if the key of the node is greater than all the nodes in its left subtree and is smaller than all the nodes in its right subtree. Let's look at a binary search tree.

![image](https://user-images.githubusercontent.com/42731246/195994195-1f8bfaea-8909-401e-8c6d-edee2dd0bbdd.png)















