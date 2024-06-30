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

public class MergeSortDoublyLinkedList {

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

        DoublyListNode sortedList = mergeSort(head);

        System.out.println("\nSorted Doubly Linked List:");
        printDoublyLinkedList(sortedList);
    }

    // Function to perform merge sort on a doubly linked list
    public static DoublyListNode mergeSort(DoublyListNode head) {
        // Base case: If list is empty or has only one node, return the list
        if (head == null || head.next == null) {
            return head;
        }

        // Step 1: Split the list into two halves
        DoublyListNode middle = getMiddle(head);
        DoublyListNode nextOfMiddle = middle.next;
        middle.next = null;
        nextOfMiddle.prev = null;

        // Step 2: Recursively sort the two halves
        DoublyListNode left = mergeSort(head);
        DoublyListNode right = mergeSort(nextOfMiddle);

        // Step 3: Merge the sorted halves
        DoublyListNode sortedList = merge(left, right);

        return sortedList;
    }

    // Function to find the middle node of a doubly linked list
    private static DoublyListNode getMiddle(DoublyListNode head) {
        if (head == null) {
            return head;
        }

        DoublyListNode slow = head;
        DoublyListNode fast = head.next;

        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }

        return slow;
    }

    // Function to merge two sorted doubly linked lists
    private static DoublyListNode merge(DoublyListNode left, DoublyListNode right) {
        if (left == null) {
            return right;
        }

        if (right == null) {
            return left;
        }

        DoublyListNode result;

        if (left.data <= right.data) {
            result = left;
            result.next = merge(left.next, right);
            result.next.prev = result;
        } else {
            result = right;
            result.next = merge(left, right.next);
            result.next.prev = result;
        }

        return result;
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
