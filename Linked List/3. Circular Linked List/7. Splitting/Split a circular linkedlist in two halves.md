class ListNode {
    int data;
    ListNode next;

    ListNode(int data) {
        this.data = data;
        this.next = null;
    }
}

public class SplitCircularLinkedList {

    public static void main(String[] args) {
        // Create a circular linked list: 1 -> 2 -> 3 -> 4 -> 5 -> 1 (circular)
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

        // Print original circular linked list
        System.out.println("Original Circular Linked List:");
        printCircularLinkedList(head);

        // Split the circular linked list into two halves
        ListNode[] halves = splitCircularList(head);

        // Print the first half of the circular linked list
        System.out.println("\nFirst Half of Circular Linked List:");
        printCircularLinkedList(halves[0]);

        // Print the second half of the circular linked list
        System.out.println("\nSecond Half of Circular Linked List:");
        printCircularLinkedList(halves[1]);
    }

    // Function to split a circular linked list into two halves
    public static ListNode[] splitCircularList(ListNode head) {
        if (head == null) {
            return new ListNode[]{null, null}; // If list is empty, return two null lists
        }

        ListNode[] halves = new ListNode[2];
        ListNode slow = head;
        ListNode fast = head;

        // Move fast pointer by two steps and slow pointer by one step
        // When fast reaches the end, slow will be at the middle
        while (fast.next != head && fast.next.next != head) {
            slow = slow.next;
            fast = fast.next.next;
        }

        // If there are even number of nodes, move slow one step forward
        if (fast.next.next == head) {
            slow = slow.next;
        }

        // Set halves
        halves[0] = head; // First half starts from head
        halves[1] = slow.next; // Second half starts from slow.next

        // Break the circular linkage
        slow.next = head; // End first half
        fast.next = halves[1]; // End second half

        return halves;
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
