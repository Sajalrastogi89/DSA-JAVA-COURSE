```java
class DoublyListNode {
    int data;
    DoublyListNode next;
    DoublyListNode prev;

    DoublyListNode(int data) {
        this.data = data;
        this.next = null;
        this.prev = null;
    }
}

public class InsertAfterNode {
    public static void main(String[] args) {
        // Create a sample doubly linked list: 1 <-> 2 <-> 3
        DoublyListNode head = new DoublyListNode(1);
        head.next = new DoublyListNode(2);
        head.next.prev = head;
        head.next.next = new DoublyListNode(3);
        head.next.next.prev = head.next;

        // Print the original list
        System.out.println("Original Doubly Linked List:");
        printDoublyLinkedList(head);

        // Insert a new node with data 4 after the node containing data 2
        int insertAfterValue = 2;
        head = insertAfter(head, insertAfterValue, 4);

        // Print the updated list
        System.out.println("\nDoubly Linked List After Insertion:");
        printDoublyLinkedList(head);
    }

    // Method to insert a node after a specific node in a doubly linked list
    public static DoublyListNode insertAfter(DoublyListNode head, int targetData, int newData) {
        // Create a new node
        DoublyListNode newNode = new DoublyListNode(newData);

        // Traverse the list to find the node with targetData
        DoublyListNode current = head;
        while (current != null && current.data != targetData) {
            current = current.next;
        }

        // If targetData is not found, return the original list
        if (current == null) {
            System.out.println("Node with value " + targetData + " not found.");
            return head;
        }

        // Insert newNode after current node
        newNode.prev = current;
        newNode.next = current.next;
        if (current.next != null) {
            current.next.prev = newNode;
        }
        current.next = newNode;

        return head;
    }

    // Method to print the doubly linked list
    public static void printDoublyLinkedList(DoublyListNode head) {
        DoublyListNode current = head;
        while (current != null) {
            System.out.print(current.data + " <-> ");
            current = current.next;
        }
        System.out.println("null");
    }
}
