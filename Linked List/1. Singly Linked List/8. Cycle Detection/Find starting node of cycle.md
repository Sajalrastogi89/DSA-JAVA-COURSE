```java
class ListNode {
    int data;
    ListNode next;

    ListNode(int data) {
        this.data = data;
        this.next = null;
    }
}

public class CycleDetection {
    public static void main(String[] args) {
        // Create a linked list with a cycle: 1 -> 2 -> 3 -> 4 -> 5 -> 3 (cycle)
        ListNode head = new ListNode(1);
        head.next = new ListNode(2);
        head.next.next = new ListNode(3);
        head.next.next.next = new ListNode(4);
        head.next.next.next.next = new ListNode(5);
        head.next.next.next.next.next = head.next.next; // Creates a cycle

        // Detect cycle and find the starting node of the cycle
        ListNode startNode = detectCycleStart(head);
        
        if (startNode != null) {
            System.out.println("Starting node of the cycle: " + startNode.data);
        } else {
            System.out.println("No cycle found in the linked list.");
        }
    }

    // Method to detect cycle in a linked list using Floyd's Cycle Detection Algorithm
    // and find the starting node of the cycle
    public static ListNode detectCycleStart(ListNode head) {
        if (head == null || head.next == null) {
            return null; // No cycle if the list is empty or has only one node
        }

        ListNode slow = head;
        ListNode fast = head;
        boolean hasCycle = false;

        // Move slow pointer by one step and fast pointer by two steps
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;

            // If slow and fast pointers meet, there is a cycle
            if (slow == fast) {
                hasCycle = true;
                break;
            }
        }

        // If no cycle is detected, return null
        if (!hasCycle) {
            return null;
        }

        // Move one pointer to the head and keep the other at the meeting point
        slow = head;
        while (slow != fast) {
            slow = slow.next;
            fast = fast.next;
        }

        // Now slow and fast pointers are at the starting node of the cycle
        return slow;
    }
}
