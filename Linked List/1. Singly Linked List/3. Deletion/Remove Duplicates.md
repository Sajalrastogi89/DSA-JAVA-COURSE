# Java Code for Removing Duplicates from a Sorted Linked List

Below is the complete Java code to define a singly linked list and remove duplicates from it. This implementation assumes that the linked list is sorted in ascending order.

```java
class ListNode {
    int data;
    ListNode next;

    ListNode(int data) {
        this.data = data;
        this.next = null;
    }
}

public class LinkedListDemo {
    public static void main(String[] args) {
        // Create a sorted linked list with duplicates: 10 -> 20 -> 20 -> 30 -> 30 -> 40
        ListNode head = new ListNode(10);
        head.next = new ListNode(20);
        head.next.next = new ListNode(20);
        head.next.next.next = new ListNode(30);
        head.next.next.next.next = new ListNode(30);
        head.next.next.next.next.next = new ListNode(40);

        // Remove duplicates from the sorted linked list
        head = removeDuplicates(head);

        // Print the updated linked list: Expected output: 10 -> 20 -> 30 -> 40
        printLinkedList(head);
    }

    // Method to remove duplicates from a sorted linked list
    public static ListNode removeDuplicates(ListNode head) {
        ListNode current = head;

        // Traverse the list
        while (current != null && current.next != null) {
            // Compare current node with its next node
            if (current.data == current.next.data) {
                current.next = current.next.next; // Skip duplicate node
            } else {
                current = current.next; // Move to the next node
            }
        }

        return head;
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
