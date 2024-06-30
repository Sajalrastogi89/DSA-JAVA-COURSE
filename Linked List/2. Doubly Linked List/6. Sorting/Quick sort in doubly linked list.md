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

public class QuickSortDoublyLinkedList {

    public static void main(String[] args) {
        // Create a sample doubly linked list: 4 <-> 2 <-> 1 <-> 3 <-> 5
        DoublyListNode head = new DoublyListNode(4);
        DoublyListNode node2 = new DoublyListNode(2);
        DoublyListNode node1 = new DoublyListNode(1);
        DoublyListNode node3 = new DoublyListNode(3);
        DoublyListNode node5 = new DoublyListNode(5);

        head.next = node2;
        node2.prev = head;
        node2.next = node1;
        node1.prev = node2;
        node1.next = node3;
        node3.prev = node1;
        node3.next = node5;
        node5.prev = node3;

        System.out.println("Original Doubly Linked List:");
        printDoublyLinkedList(head);

        quickSort(head, null);

        System.out.println("\nSorted Doubly Linked List:");
        printDoublyLinkedList(head);
    }

    // Function to perform quick sort on a doubly linked list
    public static void quickSort(DoublyListNode head, DoublyListNode end) {
        if (head != end && head != null && head.next != end) {
            DoublyListNode pivot = partition(head, end);
            quickSort(head, pivot);
            quickSort(pivot.next, end);
        }
    }

    // Function to partition the doubly linked list around a pivot
    private static DoublyListNode partition(DoublyListNode head, DoublyListNode end) {
        int pivot = end.data;
        DoublyListNode i = head.prev;

        for (DoublyListNode j = head; j != end; j = j.next) {
            if (j.data <= pivot) {
                i = (i == null) ? head : i.next;
                swapData(i, j);
            }
        }

        i = (i == null) ? head : i.next;
        swapData(i, end);
        return i;
    }

    // Function to swap data between two nodes
    private static void swapData(DoublyListNode node1, DoublyListNode node2) {
        int temp = node1.data;
        node1.data = node2.data;
        node2.data = temp;
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
