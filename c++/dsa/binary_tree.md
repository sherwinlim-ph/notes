# bst basic node structure(avoid garbage data)

struct Node {
    int data;
    Node* left;
    Node* right;

    explicit Node(int value) : data(value), left(nullptr), right(nullptr) {}
};

// void takeNode(Node n);
// takeNode(10);        // Error with `explicit` (safe: no accidental conversion)
// takeNode(Node(10));  // OK: explicit construction

# aggregate struct no constructor

// Aggregate struct with no custom constructor.
struct Node {
    int data;
    Node* left;
    Node* right;
};

// Usage: data = 10, left = nullptr, right = nullptr.
Node root{10};
Node* child = new Node{5};

# bst with include <memory>

#include <memory>

// Node owning its left and right children via unique_ptr.
struct Node {
    int data;
    std::unique_ptr<Node> left;
    std::unique_ptr<Node> right;

    explicit Node(int value) : data(value), left(nullptr), right(nullptr) {}
};

// Usage: no manual `delete` required.
auto root = std::make_unique<Node>(10);
root->left = std::make_unique<Node>(5);
root->right = std::make_unique<Node>(15);


In C++, <memory> is a standard library header file that provides tools for dynamic memory management—most notably smart pointers like std::unique_ptr and std::shared_ptr.

A std::unique_ptr is a smart pointer that exclusively owns a dynamically allocated object on the heap. When that std::unique_ptr goes out of scope (or is reassigned/destroyed), it automatically calls delete on the object, helping prevent memory leaks without requiring manual delete calls.

# bst with custom data

// Generic BST node supporting any type T.
template <typename T>
struct Node {
    T data;
    Node* left;
    Node* right;

    explicit Node(const T& value) : data(value), left(nullptr), right(nullptr) {}
};

// Usage:
Node<int> intNode(10);
Node<double> doubleNode(3.14);

# inserting a 



