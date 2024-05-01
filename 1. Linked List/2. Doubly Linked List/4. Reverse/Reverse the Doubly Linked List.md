```java
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

public class ReverseDoublyLinkedList {
    public static void main(String[] args) {
        // Create a sample doubly linked list: 1 <-> 2 <-> 3 <-> 4 <-> 5
        DoublyListNode head = new DoublyListNode(1);
        head.next = new DoublyListNode(2);
        head.next.prev = head;
        head.next.next = new DoublyListNode(3);
        head.next.next.prev = head.next;
        head.next.next.next = new DoublyListNode(4);
        head.next.next.next.prev = head.next.next;
        head.next.next.next.next = new DoublyListNode(5);
        head.next.next.next.next.prev = head.next.next.next;

        // Print the original list
        System.out.println("Original Doubly Linked List:");
        printDoublyLinkedList(head);

        // Reverse the linked list
        DoublyListNode reversedHead = reverseDoublyLinkedList(head);

        // Print the reversed list
        System.out.println("\nReversed Doubly Linked List:");
        printDoublyLinkedList(reversedHead);
    }

    // Function to reverse a doubly linked list
    public static DoublyListNode reverseDoublyLinkedList(DoublyListNode head) {
        // If the list is empty or has only one node
        if (head == null || head.next == null) {
            return head;
        }

        DoublyListNode current = head;
        DoublyListNode prev = null;

        while (current != null) {
            // Swap next and prev pointers of the current node
            DoublyListNode nextNode = current.next;
            current.next = prev;
            current.prev = nextNode;

            // Move to next node
            prev = current;
            current = nextNode;
        }

        // 'prev' is now the new head of the reversed list
        return prev;
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
