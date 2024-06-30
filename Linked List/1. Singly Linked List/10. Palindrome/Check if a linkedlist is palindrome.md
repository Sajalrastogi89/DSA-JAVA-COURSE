```java
class ListNode {
    int data;
    ListNode next;

    ListNode(int data) {
        this.data = data;
        this.next = null;
    }
}

public class PalindromeLinkedList {
    public static void main(String[] args) {
        // Create a linked list: 1 -> 2 -> 3 -> 2 -> 1
        ListNode head = new ListNode(1);
        head.next = new ListNode(2);
        head.next.next = new ListNode(3);
        head.next.next.next = new ListNode(2);
        head.next.next.next.next = new ListNode(1);

        // Check if the linked list is a palindrome
        boolean isPalindrome = isPalindrome(head);

        if (isPalindrome) {
            System.out.println("The linked list is a palindrome.");
        } else {
            System.out.println("The linked list is not a palindrome.");
        }
    }

    // Method to check if the linked list is a palindrome
    public static boolean isPalindrome(ListNode head) {
        if (head == null || head.next == null) {
            return true; // An empty list or single node list is a palindrome
        }

        // Find the middle of the linked list
        ListNode slow = head;
        ListNode fast = head;
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }

        // Reverse the second half of the linked list
        ListNode secondHalfHead = reverseList(slow);

        // Compare the first and second halves
        ListNode firstHalfHead = head;
        ListNode secondHalfIterator = secondHalfHead;
        while (secondHalfIterator != null) {
            if (firstHalfHead.data != secondHalfIterator.data) {
                // Restore the second half (optional step)
                reverseList(secondHalfHead);
                return false; // Not a palindrome
            }
            firstHalfHead = firstHalfHead.next;
            secondHalfIterator = secondHalfIterator.next;
        }

        // Restore the second half (optional step)
        reverseList(secondHalfHead);

        return true; // The linked list is a palindrome
    }

    // Method to reverse a linked list and return the new head
    public static ListNode reverseList(ListNode head) {
        ListNode prev = null;
        ListNode current = head;
        while (current != null) {
            ListNode next = current.next;
            current.next = prev;
            prev = current;
            current = next;
        }
        return prev;
    }

    // Method to print the linked list (for debugging purposes)
    public static void printLinkedList(ListNode head) {
        ListNode current = head;
        while (current != null) {
            System.out.print(current.data + " -> ");
            current = current.next;
        }
        System.out.println("null");
    }
}
