class ListNode {
    int data;
    ListNode next;

    ListNode(int data) {
        this.data = data;
        this.next = null;
    }
}

public class SplitLinkedList {
    public static void main(String[] args) {
        // Create a sample linked list: 1 -> 2 -> 3 -> 4 -> 5
        ListNode head = new ListNode(1);
        head.next = new ListNode(2);
        head.next.next = new ListNode(3);
        head.next.next.next = new ListNode(4);
        head.next.next.next.next = new ListNode(5);

        // Split the linked list into two halves
        ListNode[] halves = splitLinkedList(head);

        // Print the first half of the linked list
        System.out.println("First half of the linked list:");
        printLinkedList(halves[0]);

        // Print the second half of the linked list
        System.out.println("\nSecond half of the linked list:");
        printLinkedList(halves[1]);
    }

    // Method to split a linked list into two halves
    public static ListNode[] splitLinkedList(ListNode head) {
        if (head == null || head.next == null) {
            return new ListNode[]{head, null}; // Handle edge cases
        }

        ListNode slow = head;
        ListNode fast = head;
        ListNode prev = null;

        // Use slow and fast pointers to find the midpoint
        while (fast != null && fast.next != null) {
            prev = slow;
            slow = slow.next;
            fast = fast.next.next;
        }

        // Split the list into two halves
        prev.next = null; // Terminate the first half

        return new ListNode[]{head, slow}; // Return the heads of the two halves
    }

    // Method to print the linked list
    public static void printLinkedList(ListNode head) {
        ListNode current = head;
        while (current != null) {
            System.out.print(current.data + " -> ");
            current = current.next;
        }
        System.out.println("null");
    }
}
