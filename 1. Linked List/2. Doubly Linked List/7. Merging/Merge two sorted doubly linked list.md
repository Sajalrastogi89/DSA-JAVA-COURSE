```java
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

public class MergeSortedDoublyLinkedLists {

    public static void main(String[] args) {
        // Create two sample sorted doubly linked lists
        // List 1: 1 <-> 3 <-> 5
        DoublyListNode head1 = new DoublyListNode(1);
        DoublyListNode node3_1 = new DoublyListNode(3);
        DoublyListNode node5 = new DoublyListNode(5);

        head1.next = node3_1;
        node3_1.prev = head1;
        node3_1.next = node5;
        node5.prev = node3_1;

        // List 2: 2 <-> 4 <-> 6
        DoublyListNode head2 = new DoublyListNode(2);
        DoublyListNode node4 = new DoublyListNode(4);
        DoublyListNode node6 = new DoublyListNode(6);

        head2.next = node4;
        node4.prev = head2;
        node4.next = node6;
        node6.prev = node4;

        System.out.println("Original Doubly Linked Lists:");
        System.out.print("List 1: ");
        printDoublyLinkedList(head1);
        System.out.print("List 2: ");
        printDoublyLinkedList(head2);

        // Merge the two sorted lists
        DoublyListNode mergedHead = mergeSortedLists(head1, head2);

        System.out.println("\nMerged Sorted Doubly Linked List:");
        printDoublyLinkedList(mergedHead);
    }

    // Function to merge two sorted doubly linked lists
    public static DoublyListNode mergeSortedLists(DoublyListNode head1, DoublyListNode head2) {
        // If either list is empty, return the other list
        if (head1 == null) return head2;
        if (head2 == null) return head1;

        // Initialize pointers for traversal
        DoublyListNode dummyHead = new DoublyListNode(0); // Dummy node to facilitate merging
        DoublyListNode current = dummyHead;

        DoublyListNode p1 = head1;
        DoublyListNode p2 = head2;

        // Traverse both lists and merge them
        while (p1 != null && p2 != null) {
            if (p1.data <= p2.data) {
                current.next = p1;
                p1.prev = current;
                p1 = p1.next;
            } else {
                current.next = p2;
                p2.prev = current;
                p2 = p2.next;
            }
            current = current.next;
        }

        // Append the remaining nodes of list 1 or list 2
        if (p1 != null) {
            current.next = p1;
            p1.prev = current;
        } else {
            current.next = p2;
            p2.prev = current;
        }

        // Skip dummy head and return the merged list
        DoublyListNode mergedHead = dummyHead.next;
        mergedHead.prev = null; // Remove the previous link of the new head

        return mergedHead;
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
