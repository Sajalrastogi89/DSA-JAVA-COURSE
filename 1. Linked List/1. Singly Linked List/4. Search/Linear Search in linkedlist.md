# Java Code for Linear Search in a Linked List

Below is the complete Java code to define a singly linked list and perform linear search to find a specific value in the list.

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
        // Create a linked list: 10 -> 20 -> 30 -> 40 -> 50
        ListNode head = new ListNode(10);
        head.next = new ListNode(20);
        head.next.next = new ListNode(30);
        head.next.next.next = new ListNode(40);
        head.next.next.next.next = new ListNode(50);

        int searchValue = 30;

        // Perform linear search to find the value 30
        ListNode result = linearSearch(head, searchValue);

        if (result != null) {
            System.out.println("Value " + searchValue + " found in the linked list.");
        } else {
            System.out.println("Value " + searchValue + " not found in the linked list.");
        }
    }

    // Method to perform linear search in a linked list
    public static ListNode linearSearch(ListNode head, int value) {
        ListNode current = head;

        // Traverse the list
        while (current != null) {
            if (current.data == value) {
                return current; // Found the value, return the node
            }
            current = current.next;
        }

        return null; // Value not found
    }
}
