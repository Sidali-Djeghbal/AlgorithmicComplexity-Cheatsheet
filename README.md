# Binary Search Tree (BST) Cheatsheet

A **Binary Search Tree (BST)** is a data structure used for organizing and managing data in a hierarchical manner. Below is a C program that demonstrates the basic operations in a BST, including insertion, deletion, and traversal.

## Program Overview
```c
#include <stdio.h>
#include <stdlib.h>

// Define the structure of a BST node
struct Node {
    int key;
    struct Node *left, *right;
};

// Create a new node
struct Node* newNode(int key) {
    struct Node* node = (struct Node*)malloc(sizeof(struct Node));
    node->key = key;
    node->left = node->right = NULL;
    return node;
}

// Insert a key into the BST
struct Node* insert(struct Node* root, int key) {
    if (root == NULL) return newNode(key); // Create a new node if the tree is empty
    if (key < root->key)
        root->left = insert(root->left, key); // Insert in the left subtree if key is smaller
    else if (key > root->key)
        root->right = insert(root->right, key); // Insert in the right subtree if key is larger
    return root; // Return the unchanged root
}

// Search for a key in the BST
struct Node* search(struct Node* root, int key) {
    if (root == NULL || root->key == key) // Return the node if found or NULL if not found
        return root;
    if (key < root->key)
        return search(root->left, key); // Search in the left subtree if key is smaller
    return search(root->right); // Search in the right subtree otherwise
}

// Find the minimum value node
struct Node* findMin(struct Node* root) {
    while (root->left != NULL)
        root = root->left; // Move to the leftmost node
    return root;
}

// Delete a key from the BST
struct Node* deleteNode(struct Node* root, int key) {
    if (root == NULL) return root; // If tree is empty

    if (key < root->key)
        root->left = deleteNode(root->left, key); // Recur for the left subtree
    else if (key > root->key)
        root->right = deleteNode(root->right, key); // Recur for the right subtree
    else {
        // Node with one child or no child
        if (root->left == NULL) {
            struct Node* temp = root->right;
            free(root);
            return temp;
        } else if (root->right == NULL) {
            struct Node* temp = root->left;
            free(root);
            return temp;
        }

        // Node with two children: Get the inorder successor (smallest in the right subtree)
        struct Node* temp = findMin(root->right);

        // Copy the inorder successor's content to this node
        root->key = temp->key;

        // Delete the inorder successor
        root->right = deleteNode(root->right, temp->key);
    }
    return root;
}

// Inorder traversal (sorted order)
void inorder(struct Node* root) {
    if (root != NULL) {
        inorder(root->left); // Visit left subtree
        printf("%d ", root->key); // Print the key
        inorder(root->right); // Visit right subtree
    }
}

// Preorder traversal
void preorder(struct Node* root) {
    if (root != NULL) {
        printf("%d ", root->key); // Print the key
        preorder(root->left); // Visit left subtree
        preorder(root->right); // Visit right subtree
    }
}

// Postorder traversal
void postorder(struct Node* root) {
    if (root != NULL) {
        postorder(root->left); // Visit left subtree
        postorder(root->right); // Visit right subtree
        printf("%d ", root->key); // Print the key
    }
}

int main() {
    struct Node* root = NULL;

    // Insert nodes into the BST
    root = insert(root, 50); // Initial tree:
                             //     50
    insert(root, 30);        //     50
                             //    /
                             //   30
    insert(root, 20);        //     50
                             //    /
                             //   30
                             //  /
                             // 20
    insert(root, 40);        //     50
                             //    /
                             //   30
                             //  /  \
                             // 20   40
    insert(root, 70);        //     50
                             //    /  \
                             //   30   70
                             //  /  \
                             // 20   40
    insert(root, 60);        //     50
                             //    /  \
                             //   30   70
                             //  /  \  /
                             // 20   40 60
    insert(root, 80);        //     50
                             //    /  \
                             //   30   70
                             //  /  \  / \
                             // 20   40 60 80

    printf("Inorder traversal: ");
    inorder(root);
    printf("\n");

    printf("Preorder traversal: ");
    preorder(root);
    printf("\n");

    printf("Postorder traversal: ");
    postorder(root);
    printf("\n");

    // Delete nodes and show changes
    printf("\nDelete 20\n");
    root = deleteNode(root, 20); // Tree after deleting 20
                                 //     50
                                 //    /  \
                                 //   30   70
                                 //     \  / \
                                 //     40 60 80
    printf("Inorder traversal: ");
    inorder(root);
    printf("\n");

    printf("\nDelete 30\n");
    root = deleteNode(root, 30); // Tree after deleting 30
                                 //     50
                                 //    /  \
                                 //   40   70
                                 //       / \
                                 //      60 80
    printf("Inorder traversal: ");
    inorder(root);
    printf("\n");

    printf("\nDelete 50\n");
    root = deleteNode(root, 50); // Tree after deleting 50
                                 //     60
                                 //    /  \
                                 //   40   70
                                 //         \
                                 //         80
    printf("Inorder traversal: ");
    inorder(root);
    printf("\n");

    return 0;
}
```

## Key Features
1. **Insertion**: Adds a new node to the BST while maintaining the BST property.
2. **Search**: Finds a node with a given key.
3. **Deletion**: Removes a node while preserving the BST structure.
4. **Traversals**:
   - **Inorder**: Left -> Root -> Right (sorted order).
   - **Preorder**: Root -> Left -> Right.
   - **Postorder**: Left -> Right -> Root.

## Diagrams for Better Understanding

### Before and After Deleting 20

**Before Deletion:**
```
    50
   /  \
  30   70
 /  \  / \
20   40 60 80
```

**After Deletion:**
```
    50
   /  \
  30   70
     \  / \
     40 60 80
```

### Before and After Deleting 30

**Before Deletion:**
```
    50
   /  \
  30   70
     \  / \
     40 60 80
```

**After Deletion:**
```
    50
   /  \
  40   70
       / \
      60 80
```

### Before and After Deleting 50

**Before Deletion:**
```
    50
   /  \
  40   70
       / \
      60 80
```

**After Deletion:**
```
    60
   /  \
  40   70
         \
         80
```

## Compilation and Execution
To compile and execute this program:
1. Save the code to a file named `bst.c`.
2. Use the following commands:
   ```bash
   gcc bst.c -o bst
  
