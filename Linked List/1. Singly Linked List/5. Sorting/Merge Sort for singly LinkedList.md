# Java Code for Merge Sort on a Singly Linked List

Below is the complete Java code to implement Merge Sort on a singly linked list.

```java
class ListNode {
    int data;
    ListNode next;

    ListNode(int data) {
        this.data = data;
        this.next = null;
    }
}

public class MergeSortLinkedList {
    public static void main(String[] args) {
        // Create an unsorted linked list: 10 -> 5 -> 30 -> 20 -> 40
        ListNode head = new ListNode(10);
        head.next = new ListNode(5);
        head.next.next = new ListNode(30);
        head.next.next.next = new ListNode(20);
        head.next.next.next.next = new ListNode(40);

        // Print the unsorted linked list
        System.out.println("Unsorted Linked List:");
        printLinkedList(head);

        // Perform merge sort on the linked list
        head = mergeSort(head);

        // Print the sorted linked list
        System.out.println("\nSorted Linked List:");
        printLinkedList(head);
    }

    // Method to perform Merge Sort on a linked list
    public static ListNode mergeSort(ListNode head) {
        // Base case: If the list is empty or has only one node
        if (head == null || head.next == null) {
            return head;
        }

        // Step 1: Split the list into two halves
        ListNode middle = findMiddle(head);
        ListNode nextToMiddle = middle.next;
        middle.next = null;

        // Step 2: Recursively sort each half
        ListNode left = mergeSort(head);
        ListNode right = mergeSort(nextToMiddle);

        // Step 3: Merge the sorted halves
        ListNode sortedList = merge(left, right);

        return sortedList;
    }

    // Helper method to find the middle node of the linked list
    public static ListNode findMiddle(ListNode head) {
        if (head == null) {
            return head;
        }
        ListNode slow = head;
        ListNode fast = head.next;

        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }

        return slow;
    }

    // Helper method to merge two sorted linked lists
    public static ListNode merge(ListNode left, ListNode right) {
        ListNode result = null;

        if (left == null) {
            return right;
        }
        if (right == null) {
            return left;
        }

        // Compare the data of the two lists and recursively merge
        if (left.data <= right.data) {
            result = left;
            result.next = merge(left.next, right);
        } else {
            result = right;
            result.next = merge(left, right.next);
        }

        return result;
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
