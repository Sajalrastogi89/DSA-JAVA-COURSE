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

public class DeleteSpecificNode {
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

        // Print the original list
        System.out.println("Original Doubly Linked List:");
        printDoublyLinkedList(head);

        // Delete node with value 3
        int valueToDelete = 3;
        head = deleteNode(head, valueToDelete);

        // Print the updated list
        System.out.println("\nDoubly Linked List After Deletion:");
        printDoublyLinkedList(head);
    }

    // Method to delete a specific node by its value from a doubly linked list
    public static DoublyListNode deleteNode(DoublyListNode head, int value) {
        // If the list is empty
        if (head == null) {
            System.out.println("List is empty. Nothing to delete.");
            return null;
        }

        // Traverse the list to find the node with the value to delete
        DoublyListNode current = head;
        while (current != null && current.data != value) {
            current = current.next;
        }

        // If node with the given value is not found
        if (current == null) {
            System.out.println("Node with value " + value + " not found.");
            return head;
        }

        // Adjust pointers to delete the node
        if (current.prev != null) {
            current.prev.next = current.next;
        } else {
            // If deleting the head node
            head = current.next;
        }
        
        if (current.next != null) {
            current.next.prev = current.prev;
        }

        // Clear references from the node to be deleted
        current.next = null;
        current.prev = null;

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
