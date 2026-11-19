
# linked list node
struct Node {
    int data;
    Node* next;

    // Constructor
    Node(int val) {
        data = val;     
        next = nullptr;  
    }
};

# insert data 

// Build a simple linked list: 10 -> 20 -> 30 -> nullptr
    Node* head = new Node(10);
    head->next = new Node(20);
    head->next->next = new Node(30);

// Traverse the list
    traverseList(head);

# traversing a linked list

// Traverse and print every node from head to the end of the list
void traverseList(Node* head) {
    Node* current = head; // Start at head without modifying the original head pointer

    while (current != nullptr) {
        cout << current->data << " -> "; // Access node data via pointer
        current = current->next;              // Advance to the next node
    }

    std::cout << "nullptr\n"; // Indicates the end of the list
}
