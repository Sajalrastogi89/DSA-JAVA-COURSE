```java
class ListNode {
    int data;
    ListNode next;

    ListNode(int data) {
        this.data = data;
        this.next = null;
    }
}

public class InsertAtEndCircularLinkedList {

    public static void main(String[] args) {
        // Create an empty circular linked list
        ListNode head = null;

        // Insert nodes at the end: 1 -> 2 -> 3 -> 4 -> 5
        head = insertAtEnd(head, 1);
        head = insertAtEnd(head, 2);
        head = insertAtEnd(head, 3);
        head = insertAtEnd(head, 4);
        head = insertAtEnd(head, 5);

        // Print the circular linked list
        System.out.println("Circular Linked List after insertions at end:");
        printCircularLinkedList(head);
    }

    // Function to insert a node at the end of a circular linked list
    public static ListNode insertAtEnd(ListNode head, int newData) {
        ListNode newNode = new ListNode(newData);

        if (head == null) { // If the list is empty
            newNode.next = newNode; // Point to itself
            return newNode; // newNode becomes the head
        }

        // Find the last node of the circular list
        ListNode last = head;
        while (last.next != head) {
            last = last.next;
        }

        // Insert newNode at the end
        newNode.next = head; // Connect newNode to head to make it circular
        last.next = newNode; // Update the next pointer of the last node to newNode
        return head; // head remains the same
    }

    // Function to print a circular linked list
    public static void printCircularLinkedList(ListNode head) {
        if (head == null) {
            System.out.println("Circular linked list is empty.");
            return;
        }

        ListNode current = head;
        do {
            System.out.print(current.data + " -> ");
            current = current.next;
        } while (current != head);

        System.out.println("(head)");
    }
}
