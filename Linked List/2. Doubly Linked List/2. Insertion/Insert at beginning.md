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

public class InsertAtBeginning {
    public static void main(String[] args) {
        // Create a sample doubly linked list: 2 <-> 3 <-> 4
        DoublyListNode head = new DoublyListNode(2);
        head.next = new DoublyListNode(3);
        head.next.prev = head;
        head.next.next = new DoublyListNode(4);
        head.next.next.prev = head.next;

        // Print the original list
        System.out.println("Original Doubly Linked List:");
        printDoublyLinkedList(head);

        // Insert a new node with data 1 at the beginning
        head = insertAtBeginning(head, 1);

        // Print the updated list
        System.out.println("\nDoubly Linked List After Insertion:");
        printDoublyLinkedList(head);
    }

    // Method to insert a node at the beginning of a doubly linked list
    public static DoublyListNode insertAtBeginning(DoublyListNode head, int data) {
        // Create a new node
        DoublyListNode newNode = new DoublyListNode(data);

        // Set the new node's next to the current head
        newNode.next = head;

        // Update the current head's prev to the new node, if head is not null
        if (head != null) {
            head.prev = newNode;
        }

        // The new node becomes the new head
        return newNode;
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
