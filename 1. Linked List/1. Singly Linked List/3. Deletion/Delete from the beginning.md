# Java Code for Deleting from the Beginning of a Linked List

Below is the complete Java code to define a singly linked list and delete a node from the beginning of the list.

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
        // Create an initial linked list: 10 -> 20 -> 30
        ListNode head = new ListNode(10);
        head.next = new ListNode(20);
        head.next.next = new ListNode(30);

        // Delete the node from the beginning
        head = deleteFromBeginning(head);

        // Print the linked list: Expected output: 20 -> 30
        printLinkedList(head);
    }

    // Method to delete the node from the beginning
    public static ListNode deleteFromBeginning(ListNode head) {
        // If the list is empty or has only one node
        if (head == null || head.next == null) {
            return null;
        }

        // Move the head pointer to the next node
        head = head.next;
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
