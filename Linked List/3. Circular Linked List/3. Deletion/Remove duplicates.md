class ListNode {
    int data;
    ListNode next;

    ListNode(int data) {
        this.data = data;
        this.next = null;
    }
}

public class RemoveDuplicatesCircularLinkedList {

    public static void main(String[] args) {
        // Create a circular linked list with duplicates: 1 -> 2 -> 2 -> 3 -> 3 -> 4 -> 5 -> 1
        ListNode head = new ListNode(1);
        ListNode node2 = new ListNode(2);
        ListNode node2_2 = new ListNode(2);
        ListNode node3 = new ListNode(3);
        ListNode node3_2 = new ListNode(3);
        ListNode node4 = new ListNode(4);
        ListNode node5 = new ListNode(5);

        head.next = node2;
        node2.next = node2_2;
        node2_2.next = node3;
        node3.next = node3_2;
        node3_2.next = node4;
        node4.next = node5;
        node5.next = head; // Making it circular

        // Print the original circular linked list
        System.out.println("Original Circular Linked List:");
        printCircularLinkedList(head);

        // Remove duplicates
        head = removeDuplicates(head);

        // Print the circular linked list after removing duplicates
        System.out.println("\nCircular Linked List after removing duplicates:");
        printCircularLinkedList(head);
    }

    // Function to remove duplicates from a circular linked list
    public static ListNode removeDuplicates(ListNode head) {
        if (head == null) {
            return null; // If the list is empty, return null
        }

        ListNode current = head;
        ListNode runner; // Pointer to check for duplicates

        // Traverse through the circular list
        while (current != null) {
            runner = current;

            // Check subsequent nodes for duplicates
            while (runner.next != head) {
                if (runner.next.data == current.data) {
                    runner.next = runner.next.next; // Remove duplicate node
                } else {
                    runner = runner.next;
                }
            }

            current = current.next; // Move to the next node
        }

        return head; // Return the head of the updated circular linked list
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
