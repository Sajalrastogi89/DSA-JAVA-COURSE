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

public class TraverseDoublyLinkedList {
    public static void main(String[] args) {
        // Create a sample doubly linked list: 1 <-> 2 <-> 3 <-> 4 <-> 5
        DoublyListNode head = new DoublyListNode(1);
        head.next = new DoublyListNode(2);
        head.next.prev = head;
        head.next.next = new DoublyListNode(3);
        head.next.next.prev = head.next;
        head.next.next.next = new DoublyListNode(4);
        head.next.next.next.prev = head.next.next;
        head.next.next.next.next = new DoublyListNode(5);
        head.next.next.next.next.prev = head.next.next.next;

        // Print the doubly linked list
        System.out.println("Traversing the Doubly Linked List:");
        traverseAndPrint(head);
    }

    // Method to traverse the doubly linked list and print each node's data
    public static void traverseAndPrint(DoublyListNode head) {
        DoublyListNode current = head; // Start from the head node
        while (current != null) { // Traverse until the end of the list
            System.out.print(current.data + " <-> "); // Print the data of the current node
            current = current.next; // Move to the next node
        }
        System.out.println("null"); // End of the list
    }
}
