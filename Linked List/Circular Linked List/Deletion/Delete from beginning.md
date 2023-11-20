class ListNode {
    int data;
    ListNode next;

    ListNode(int data) {
        this.data = data;
        this.next = null;
    }
}

public class DeleteFromBeginningCircularLinkedList {

    public static void main(String[] args) {
        // Create a circular linked list: 1 -> 2 -> 3 -> 4 -> 5
        ListNode head = new ListNode(1);
        ListNode node2 = new ListNode(2);
        ListNode node3 = new ListNode(3);
        ListNode node4 = new ListNode(4);
        ListNode node5 = new ListNode(5);

        head.next = node2;
        node2.next = node3;
        node3.next = node4;
        node4.next = node5;
        node5.next = head; // Making it circular

        // Delete node from the beginning
        head = deleteFromBeginning(head);

        // Print the circular linked list after deletion
        System.out.println("Circular Linked List after deletion from beginning:");
        printCircularLinkedList(head);
    }

    // Function to delete a node from the beginning of a circular linked list
    public static ListNode deleteFromBeginning(ListNode head) {
        if (head == null) {
            System.out.println("Circular linked list is empty. Nothing to delete.");
            return null;
        }

        // If there's only one node
        if (head.next == head) {
            return null; // Return null indicating empty list
        }

        // Find the last node of the circular list
        ListNode last = head;
        while (last.next != head) {
            last = last.next;
        }

        // Delete the head node
        last.next = head.next; // Update last node's next to skip the head
        return head.next; // head.next becomes the new head
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
