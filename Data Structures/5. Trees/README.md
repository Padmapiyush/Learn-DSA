# Trees in C++:

### Defining a Tree Structure:
In C++, a tree is typically defined using a struct or class that contains a data element and pointers to its left and right subtrees.

```c++
struct TreeNode {
  int data;
  TreeNode* left;
  TreeNode* right;
  TreeNode(int val) : data(val), left(nullptr), right(nullptr) {}
};
```

### Creating a Tree: 
To create a tree, we need to create its nodes and connect them together. We can do this recursively by creating the left and right subtrees and connecting them to the root node.

```c++
TreeNode* createTree() {
  int data;
  cout << "Enter data: ";
  cin >> data;

  if (data == -1) { // -1 denotes end of subtree
    return nullptr;
  }

  TreeNode* root = new TreeNode(data);
  root->left = createTree();
  root->right = createTree();

  return root;
}
```

### Traversing a Tree:
There are three main ways to traverse a tree - preorder, inorder, and postorder. In C++, we can implement these traversals recursively as follows:

```c++
void preorder(TreeNode* root) {
  if (root == nullptr) {
    return;
  }
  cout << root->data << " ";
  preorder(root->left);
  preorder(root->right);
}

void inorder(TreeNode* root) {
  if (root == nullptr) {
    return;
  }
  inorder(root->left);
  cout << root->data << " ";
  inorder(root->right);
}

void postorder(TreeNode* root) {
  if (root == nullptr) {
    return;
  }
  postorder(root->left);
  postorder(root->right);
  cout << root->data << " ";
}
```

### Tree Traversal Iteratively:
we can use a stack to implement tree traversal iteratively.

```c++
void inorderIterative(TreeNode* root) {
  stack<TreeNode*> st;
  TreeNode* curr = root;

  while (curr != nullptr || !st.empty()) {
    while (curr != nullptr) {
      st.push(curr);
      curr = curr->left;
    }

    curr = st.top();
    st.pop();
    cout << curr->data << " ";
    curr = curr->right;
  }
}
```

These are some basic notes on trees in C++. There are many more operations that can be performed on trees, including inserting and deleting nodes, finding the height and diameter of the tree, and balancing the tree.





