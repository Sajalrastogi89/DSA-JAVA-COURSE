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

public class DeleteFromEnd {
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

        // Delete the node from the end
        head = deleteFromEnd(head);

        // Print the updated list
        System.out.println("\nDoubly Linked List After Deletion:");
        printDoublyLinkedList(head);
    }

    // Method to delete a node from the end of a doubly linked list
    public static DoublyListNode deleteFromEnd(DoublyListNode head) {
        // If the list is empty
        if (head == null) {
            System.out.println("List is empty. Nothing to delete.");
            return null;
        }

        // If the list has only one node
        if (head.next == null) {
            return null;
        }

        // Traverse to the end of the list
        DoublyListNode current = head;
        while (current.next != null) {
            current = current.next;
        }

        // Adjust pointers to delete the last node
        if (current.prev != null) {
            current.prev.next = null;
        } else {
            // If current is the head (list had exactly one node)
            head = null;
        }

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
