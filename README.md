
A **linked list** is a linear data structure where elements are stored in nodes, and each node points to the next node in the sequence. Unlike arrays, linked lists do not require contiguous memory allocation, which allows for dynamic memory usage.

### Key Concepts of Linked Lists

1. **Node**: A basic unit of a linked list containing:
   - **Data**: The value stored in the node.
   - **Next**: A reference (or link) to the next node in the list.

2. **Head**: The first node in the linked list. It is used to access the list.

3. **Tail**: The last node in the linked list, which points to `null`.

4. **Singly Linked List**: Each node points to the next node.
5. **Doubly Linked List**: Each node points to both the next and the previous nodes.

### Singly Linked List Implementation in Java

Here's a simple implementation of a singly linked list in Java:

```java
// Node class
class Node {
    int data;
    Node next;  // Reference to the next node

    // Constructor to initialize a new node
    Node(int data) {
        this.data = data;
        this.next = null;
    }
}

// LinkedList class
class LinkedList {
    Node head;  // Head of the linked list

    // Method to add a node to the end of the linked list
    public void add(int data) {
        Node newNode = new Node(data);  // Create a new node

        if (head == null) {  // If the list is empty, make the new node the head
            head = newNode;
        } else {
            Node current = head;
            while (current.next != null) {  // Traverse to the end of the list
                current = current.next;
            }
            current.next = newNode;  // Add the new node at the end
        }
    }

    // Method to print all the nodes in the linked list
    public void printList() {
        Node current = head;
        while (current != null) {  // Traverse the list
            System.out.print(current.data + " -> ");
            current = current.next;
        }
        System.out.println("null");
    }

    // Method to delete a node by its value
    public void delete(int key) {
        Node current = head, prev = null;

        // If the head node itself holds the key to be deleted
        if (current != null && current.data == key) {
            head = current.next;  // Change head
            return;
        }

        // Search for the key to be deleted
        while (current != null && current.data != key) {
            prev = current;
            current = current.next;
        }

        // If the key was not present in the linked list
        if (current == null) return;

        // Unlink the node from the linked list
        prev.next = current.next;
    }
}

// Main class to test the LinkedList
public class Main {
    public static void main(String[] args) {
        LinkedList list = new LinkedList();
        list.add(1);
        list.add(2);
        list.add(3);
        list.add(4);

        System.out.println("Original Linked List:");
        list.printList();

        list.delete(3);
        System.out.println("Linked List after deleting 3:");
        list.printList();
    }
}
```

### Explanation

1. **Node Class**: This class represents a node in a linked list. Each node has two fields: `data` (the value it holds) and `next` (a reference to the next node).

2. **LinkedList Class**: This class contains the methods to manipulate the linked list:
   - **add(int data)**: Adds a new node with the given data to the end of the list.
   - **printList()**: Prints the entire linked list.
   - **delete(int key)**: Deletes the first occurrence of a node with the given key.

3. **Main Class**: The `Main` class demonstrates how to use the linked list. It creates a linked list, adds some nodes, prints it, deletes a node, and prints the updated list.

### Key Points

- Linked lists are great for dynamic data scenarios where the size of the data can change.
- Linked lists are not efficient for random access; they are better suited for sequential access.
- Each element in a linked list is a separate object (node), and the list's overall memory usage is not contiguous.

If you have any questions or want to learn more about other types of linked lists (like doubly linked lists or circular linked lists), let me know!
