class ListNode {
    int data;
    ListNode next;

    ListNode(int data) {
        this.data = data;
        this.next = null;
    }
}

public class ReverseLinkedList {
    public static void main(String[] args) {
        // Create a sample linked list: 1 -> 2 -> 3 -> 4 -> 5
        ListNode head = new ListNode(1);
        head.next = new ListNode(2);
        head.next.next = new ListNode(3);
        head.next.next.next = new ListNode(4);
        head.next.next.next.next = new ListNode(5);

        // Print the original linked list
        System.out.println("Original Linked List:");
        printLinkedList(head);

        // Reverse the linked list using iterative method
        ListNode reversedHeadIterative = reverseLinkedListIterative(head);

        // Print the reversed linked list (iterative)
        System.out.println("\nReversed Linked List (Iterative):");
        printLinkedList(reversedHeadIterative);

        // Reset the list to original
        head = reverseLinkedListIterative(reversedHeadIterative);

        // Reverse the linked list using recursive method
        ListNode reversedHeadRecursive = reverseLinkedListRecursive(head);

        // Print the reversed linked list (recursive)
        System.out.println("\nReversed Linked List (Recursive):");
        printLinkedList(reversedHeadRecursive);
    }

    // Iterative method to reverse a linked list
    public static ListNode reverseLinkedListIterative(ListNode head) {
        ListNode prev = null;
        ListNode current = head;
        while (current != null) {
            ListNode next = current.next; // Save the next node
            current.next = prev; // Reverse the link
            prev = current; // Move prev to current node
            current = next; // Move to the next node
        }
        return prev; // prev becomes the new head
    }

    // Recursive method to reverse a linked list
    public static ListNode reverseLinkedListRecursive(ListNode head) {
        // Base case: if head is empty or only one node, it's reversed
        if (head == null || head.next == null) {
            return head;
        }
        
        // Recursive step: reverse the rest of the list
        ListNode newHead = reverseLinkedListRecursive(head.next);
        
        // Reverse the link of current node
        head.next.next = head;
        head.next = null;
        
        return newHead; // Return new head of the reversed list
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
