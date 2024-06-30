```java
class ListNode {
    int data;
    ListNode next;

    ListNode(int data) {
        this.data = data;
        this.next = null;
    }
}

public class FindMiddleCircularLinkedList {

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

        ListNode middle = findMiddle(head);

        System.out.println("Middle element of the circular linked list: " + middle.data);
    }

    // Function to find the middle element of a circular linked list
    public static ListNode findMiddle(ListNode head) {
        if (head == null) {
            return null; // If list is empty
        }

        ListNode slow = head;
        ListNode fast = head;

        // Move fast pointer by two steps and slow pointer by one step
        // When fast reaches the end, slow will be at the middle
        while (fast != null && fast.next != head && fast.next.next != head) {
            slow = slow.next;
            fast = fast.next.next;
        }

        // If there are even number of nodes, return the second middle node
        if (fast.next.next == head) {
            slow = slow.next;
        }

        return slow; // Return the middle node
    }
}
