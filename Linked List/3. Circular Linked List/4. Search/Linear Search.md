```java
class ListNode {
    int data;
    ListNode next;

    ListNode(int data) {
        this.data = data;
        this.next = null;
    }
}

public class LinearSearchCircularLinkedList {

    public static void main(String[] args) {
        // Create a circular linked list: 1 -> 2 -> 3 -> 4 -> 5 -> 1 (circular)
        ListNode head = new ListNode(1);
        ListNode node2 = new ListNode(2);
        ListNode node3 = new ListNode(3);
        ListNode node4 = new ListNode(4);
        ListNode node5 = new ListNode(5);

        head.next = node2;
        node2.next = node3;
        node3.next = node4;
        node4.next = node5;
        node5.next = head; // Making it circular

        int target = 3;
        boolean found = linearSearch(head, target);

        if (found) {
            System.out.println("Element " + target + " found in the circular linked list.");
        } else {
            System.out.println("Element " + target + " not found in the circular linked list.");
        }
    }

    // Function to perform linear search in a circular linked list
    public static boolean linearSearch(ListNode head, int target) {
        if (head == null) {
            return false; // If the list is empty, return false
        }

        ListNode current = head;

        // Traverse through the circular list
        do {
            if (current.data == target) {
                return true; // Element found
            }
            current = current.next;
        } while (current != head);

        return false; // Element not found in the circular linked list
    }
}
