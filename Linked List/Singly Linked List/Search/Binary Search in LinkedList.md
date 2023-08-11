# Java Code for Binary Search in a Sorted Linked List

Below is the complete Java code to define a sorted singly linked list and perform binary search based on indices.

```java
class ListNode {
    int data;
    ListNode next;

    ListNode(int data) {
        this.data = data;
        this.next = null;
    }
}

public class SortedLinkedListDemo {
    public static void main(String[] args) {
        // Create a sorted linked list: 10 -> 20 -> 30 -> 40 -> 50
        ListNode head = new ListNode(10);
        head.next = new ListNode(20);
        head.next.next = new ListNode(30);
        head.next.next.next = new ListNode(40);
        head.next.next.next.next = new ListNode(50);

        int searchValue = 30;

        // Perform binary search to find the value 30
        ListNode result = binarySearch(head, searchValue);

        if (result != null) {
            System.out.println("Value " + searchValue + " found in the sorted linked list.");
        } else {
            System.out.println("Value " + searchValue + " not found in the sorted linked list.");
        }
    }

    // Method to perform binary search in a sorted linked list based on indices
    public static ListNode binarySearch(ListNode head, int value) {
        // Count the number of nodes
        int count = 0;
        ListNode current = head;
        while (current != null) {
            count++;
            current = current.next;
        }

        // Perform binary search based on indices
        int low = 0;
        int high = count - 1;

        while (low <= high) {
            int mid = low + (high - low) / 2;
            ListNode midNode = getNodeAt(head, mid);

            if (midNode.data == value) {
                return midNode;
            } else if (midNode.data < value) {
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }

        return null; // Value not found
    }

    // Helper method to get the node at a specific index
    public static ListNode getNodeAt(ListNode head, int index) {
        ListNode current = head;
        for (int i = 0; i < index && current != null; i++) {
            current = current.next;
        }
        return current;
    }
}
