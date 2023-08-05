# Java Code for Inserting After a Specific Node in a Linked List

Below is the complete Java code to define a singly linked list and insert a new node after a specific node.

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

        // Insert a new node with value 25 after the node with value 20
        insertAfter(head, 20, 25);

        // Print the linked list: Expected output: 10 -> 20 -> 25 -> 30
        printLinkedList(head);
    }

    // Method to insert a new node after a node with a specific value
    public static void insertAfter(ListNode head, int targetData, int newData) {
        ListNode current = head;

        // Traverse the list to find the target node
        while (current != null && current.data != targetData) {
            current = current.next;
        }

        // If the target node is found, insert the new node after it
        if (current != null) {
            ListNode newNode = new ListNode(newData);
            newNode.next = current.next;
            current.next = newNode;
        }
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
