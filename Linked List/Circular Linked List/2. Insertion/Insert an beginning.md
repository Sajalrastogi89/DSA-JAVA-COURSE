class ListNode {
    int data;
    ListNode next;

    ListNode(int data) {
        this.data = data;
        this.next = null;
    }
}

public class InsertAtBeginningCircularLinkedList {

    public static void main(String[] args) {
        // Create an empty circular linked list
        ListNode head = null;

        // Insert nodes at the beginning: 5 -> 4 -> 3 -> 2 -> 1
        head = insertAtBeginning(head, 1);
        head = insertAtBeginning(head, 2);
        head = insertAtBeginning(head, 3);
        head = insertAtBeginning(head, 4);
        head = insertAtBeginning(head, 5);

        // Print the circular linked list
        System.out.println("Circular Linked List after insertions:");
        printCircularLinkedList(head);
    }

    // Function to insert a node at the beginning of a circular linked list
    public static ListNode insertAtBeginning(ListNode head, int newData) {
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

        // Insert newNode at the beginning
        newNode.next = head;
        last.next = newNode; // Update the last node's next to newNode
        return newNode; // newNode becomes the new head
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
