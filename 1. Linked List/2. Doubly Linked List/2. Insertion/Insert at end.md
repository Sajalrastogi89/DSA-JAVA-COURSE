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

public class InsertAtEnd {
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

        // Insert a new node with data 4 at the end
        head = insertAtEnd(head, 4);

        // Print the updated list
        System.out.println("\nDoubly Linked List After Insertion:");
        printDoublyLinkedList(head);
    }

    // Method to insert a node at the end of a doubly linked list
    public static DoublyListNode insertAtEnd(DoublyListNode head, int data) {
        // Create a new node
        DoublyListNode newNode = new DoublyListNode(data);

        // If the list is empty, the new node becomes the head
        if (head == null) {
            return newNode;
        }

        // Traverse to the end of the list
        DoublyListNode current = head;
        while (current.next != null) {
            current = current.next;
        }

        // Link the new node at the end
        current.next = newNode;
        newNode.prev = current;

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
