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

public class TraverseDoublyLinkedListBackward {
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

        // Print the doubly linked list backward
        System.out.println("Traversing the Doubly Linked List Backward:");
        traverseBackwardAndPrint(head);
    }

    // Method to traverse the doubly linked list backward and print each node's data
    public static void traverseBackwardAndPrint(DoublyListNode head) {
        if (head == null) {
            System.out.println("The list is empty.");
            return;
        }

        // Move to the last node
        DoublyListNode current = head;
        while (current.next != null) {
            current = current.next;
        }

        // Traverse backward from the last node to the head
        while (current != null) {
            System.out.print(current.data + " <-> ");
            current = current.prev;
        }
        System.out.println("null"); // End of the list
    }
}
