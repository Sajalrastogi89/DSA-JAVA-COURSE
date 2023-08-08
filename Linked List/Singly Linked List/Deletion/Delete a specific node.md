# Java Code for Deleting a Specific Node from a Linked List

Below is the complete Java code to define a singly linked list and delete a specific node by its value.

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
        // Create an initial linked list: 10 -> 20 -> 30 -> 40
        ListNode head = new ListNode(10);
        head.next = new ListNode(20);
        head.next.next = new ListNode(30);
        head.next.next.next = new ListNode(40);

        // Delete the node with value 30
        head = deleteNode(head, 30);

        // Print the linked list: Expected output: 10 -> 20 -> 40
        printLinkedList(head);
    }

    // Method to delete a specific node by its value
    public static ListNode deleteNode(ListNode head, int value) {
        // Handle case where the node to be deleted is the head
        if (head != null && head.data == value) {
            return head.next;
        }

        ListNode current = head;
        ListNode prev = null;

        // Traverse the list to find the node to delete
        while (current != null && current.data != value) {
            prev = current;
            current = current.next;
        }

        // If the node was found, delete it
        if (current != null) {
            prev.next = current.next;
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
