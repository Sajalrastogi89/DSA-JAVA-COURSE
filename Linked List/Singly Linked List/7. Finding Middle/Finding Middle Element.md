class ListNode {
    int data;
    ListNode next;

    ListNode(int data) {
        this.data = data;
        this.next = null;
    }
}

public class MiddleElementLinkedList {
    public static void main(String[] args) {
        // Create a linked list: 10 -> 20 -> 30 -> 40 -> 50
        ListNode head = new ListNode(10);
        head.next = new ListNode(20);
        head.next.next = new ListNode(30);
        head.next.next.next = new ListNode(40);
        head.next.next.next.next = new ListNode(50);

        // Find and print the middle element
        ListNode middle = findMiddle(head);
        System.out.println("Middle Element: " + middle.data);
    }

    // Method to find the middle element of a linked list
    public static ListNode findMiddle(ListNode head) {
        if (head == null) {
            return null;
        }

        ListNode slow = head;
        ListNode fast = head;

        // Move slow pointer by one step and fast pointer by two steps
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }

        // At this point, slow is at the middle node
        return slow;
    }
}
