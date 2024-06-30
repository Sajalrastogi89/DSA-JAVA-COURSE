```java
import java.util.HashSet;

class ListNode {
    int data;
    ListNode next;

    ListNode(int data) {
        this.data = data;
        this.next = null;
    }
}

public class UnionLinkedList {
    public static void main(String[] args) {
        // Create first linked list: 1 -> 2 -> 3 -> 4
        ListNode list1 = new ListNode(1);
        list1.next = new ListNode(2);
        list1.next.next = new ListNode(3);
        list1.next.next.next = new ListNode(4);

        // Create second linked list: 3 -> 4 -> 5 -> 6
        ListNode list2 = new ListNode(3);
        list2.next = new ListNode(4);
        list2.next.next = new ListNode(5);
        list2.next.next.next = new ListNode(6);

        // Compute the union of the two linked lists
        ListNode unionList = unionOfLinkedLists(list1, list2);

        // Print the union of the linked lists
        System.out.println("Union of the linked lists:");
        printLinkedList(unionList);
    }

    // Method to compute the union of two linked lists
    public static ListNode unionOfLinkedLists(ListNode list1, ListNode list2) {
        HashSet<Integer> set = new HashSet<>(); // To store unique elements
        ListNode unionHead = new ListNode(0); // Dummy head for the union list
        ListNode current = unionHead;

        // Add all elements of list1 to the set and the union list
        ListNode temp = list1;
        while (temp != null) {
            if (set.add(temp.data)) {
                current.next = new ListNode(temp.data);
                current = current.next;
            }
            temp = temp.next;
        }

        // Add all elements of list2 to the set and the union list
        temp = list2;
        while (temp != null) {
            if (set.add(temp.data)) {
                current.next = new ListNode(temp.data);
                current = current.next;
            }
            temp = temp.next;
        }

        return unionHead.next; // Return the union list, excluding the dummy head
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
