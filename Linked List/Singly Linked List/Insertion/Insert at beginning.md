# Insert at Beginning of a Linked List in Java

This code demonstrates how to insert a new node at the beginning of a singly linked list in Java.

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
        // Create an initial linked list with three nodes
        ListNode head = new ListNode(2);
        head.next = new ListNode(3);
        head.next.next = new ListNode(4);

        System.out.println("Original Linked List:");
        printLinkedList(head);

        // Insert a new node at the beginning
        head = insertAtBeginning(head, 1);

        System.out.println("\nLinked List after inserting at the beginning:");
        printLinkedList(head);
    }

    // Method to insert a new node at the beginning
    public static ListNode insertAtBeginning(ListNode head, int data) {
        ListNode newNode = new ListNode(data);
        newNode.next = head;
        return newNode;
    }

    // Method to print the linked list
    public static void printLinkedList(ListNode head) {
        ListNode current = head;
        while (current != null) {
            System.out.print(current.data + " ");
            current = current.next;
        }
        System.out.println();
    }
}
