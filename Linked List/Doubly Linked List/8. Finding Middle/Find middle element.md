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

public class FindMiddleElementDoublyLinkedList {

    public static void main(String[] args) {
        // Create a sample doubly linked list: 1 <-> 2 <-> 3 <-> 4 <-> 5
        DoublyListNode head = new DoublyListNode(1);
        DoublyListNode node2 = new DoublyListNode(2);
        DoublyListNode node3 = new DoublyListNode(3);
        DoublyListNode node4 = new DoublyListNode(4);
        DoublyListNode node5 = new DoublyListNode(5);

        head.next = node2;
        node2.prev = head;
        node2.next = node3;
        node3.prev = node2;
        node3.next = node4;
        node4.prev = node3;
        node4.next = node5;
        node5.prev = node4;

        // Print the original doubly linked list
        System.out.println("Original Doubly Linked List:");
        printDoublyLinkedList(head);

        // Find the middle element
        DoublyListNode middle = findMiddleElement(head);

        // Print the middle element
        System.out.println("\nMiddle Element: " + middle.data);
    }

    // Function to find the middle element of a doubly linked list
    public static DoublyListNode findMiddleElement(DoublyListNode head) {
        if (head == null) {
            return null;
        }

        DoublyListNode slow = head;
        DoublyListNode fast = head;

        while (fast != null && fast.next != null) {
            slow = slow.next;       // Move slow pointer by 1 step
            fast = fast.next.next;  // Move fast pointer by 2 steps
        }

        return slow;  // Return the middle element
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
