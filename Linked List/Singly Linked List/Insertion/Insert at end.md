# Java Code for Inserting at the End of a Linked List

Below is the complete Java code to define a singly linked list and insert a new node at the end of the list.

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
        // Create an initial linked list with one node
        ListNode head = new ListNode(10);

        // Insert new nodes at the end
        head = insertAtEnd(head, 20);
        head = insertAtEnd(head, 30);
        head = insertAtEnd(head, 40);

        // Print the linked list
        printLinkedList(head);
    }

    // Method to insert a new node at the end
    public static ListNode insertAtEnd(ListNode head, int data) {
        ListNode newNode = new ListNode(data);

        // If the list is empty, the new node is the head
        if (head == null) {
            return newNode;
        }

        // Traverse to the end of the list
        ListNode current = head;
        while (current.next != null) {
            current = current.next;
        }

        // Append the new node at the end
        current.next = newNode;
        return head;
    }

    // Method to print the linked list
    public static void printLinkedList(ListNode head) {
        ListNode current = head;
        while (current != null) {
            System.out.print(current.data + " ");
            current = current.next;
        }
    }
}
