class DoublyListNode {
    int data;
    DoublyListNode prev;
    DoublyListNode next;

    DoublyListNode(int data) {
        this.data = data;
        this.prev = null;
        this.next = null;
    }
}

public class PalindromeDoublyLinkedList {

    public static void main(String[] args) {
        // Create a sample doubly linked list: 1 <-> 2 <-> 3 <-> 2 <-> 1
        DoublyListNode head = new DoublyListNode(1);
        DoublyListNode node2_1 = new DoublyListNode(2);
        DoublyListNode node3 = new DoublyListNode(3);
        DoublyListNode node2_2 = new DoublyListNode(2);
        DoublyListNode node1 = new DoublyListNode(1);

        head.next = node2_1;
        node2_1.prev = head;
        node2_1.next = node3;
        node3.prev = node2_1;
        node3.next = node2_2;
        node2_2.prev = node3;
        node2_2.next = node1;
        node1.prev = node2_2;

        // Print the original doubly linked list
        System.out.println("Original Doubly Linked List:");
        printDoublyLinkedList(head);

        // Check if the list is a palindrome
        boolean isPalindrome = isPalindrome(head);

        // Print the result
        System.out.println("\nIs the list a palindrome? " + isPalindrome);
    }

    // Function to check if a doubly linked list is palindrome
    public static boolean isPalindrome(DoublyListNode head) {
        if (head == null || head.next == null) {
            return true;
        }

        // Find the tail node
        DoublyListNode tail = head;
        while (tail.next != null) {
            tail = tail.next;
        }

        // Compare nodes from head and tail towards the center
        DoublyListNode start = head;
        DoublyListNode end = tail;

        while (start != end && end.next != start) {
            if (start.data != end.data) {
                return false;
            }
            start = start.next;
            end = end.prev;
        }

        return true;
    }

    // Utility function to print the doubly linked list
    public static void printDoublyLinkedList(DoublyListNode head) {
        DoublyListNode current = head;
        while (current != null) {
            System.out.print(current.data + " <-> ");
            current = current.next;
        }
        System.out.println("null");
    }
}
