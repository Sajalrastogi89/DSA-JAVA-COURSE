class ListNode {
    int data;
    ListNode next;

    ListNode(int data) {
        this.data = data;
        this.next = null;
    }
}

public class QuickSortLinkedList {
    public static void main(String[] args) {
        // Create an unsorted linked list: 10 -> 5 -> 30 -> 20 -> 40
        ListNode head = new ListNode(10);
        head.next = new ListNode(5);
        head.next.next = new ListNode(30);
        head.next.next.next = new ListNode(20);
        head.next.next.next.next = new ListNode(40);

        // Print the unsorted linked list
        System.out.println("Unsorted Linked List:");
        printLinkedList(head);

        // Perform quick sort on the linked list
        head = quickSort(head);

        // Print the sorted linked list
        System.out.println("\nSorted Linked List:");
        printLinkedList(head);
    }

    // Method to perform Quick Sort on a linked list
    public static ListNode quickSort(ListNode head) {
        // Base case: If the list is empty or has only one node
        if (head == null || head.next == null) {
            return head;
        }

        // Step 1: Choose a pivot (here we choose the first node)
        ListNode pivot = head;
        head = head.next;
        pivot.next = null;

        // Step 2: Partition the list around the pivot
        ListNode[] partitions = partition(head, pivot.data);

        ListNode left = partitions[0];
        ListNode right = partitions[1];

        // Step 3: Recursively sort each partition
        left = quickSort(left);
        right = quickSort(right);

        // Step 4: Concatenate the sorted partitions
        pivot.next = right; // Connect pivot to the right partition
        if (left == null) {
            return pivot; // If no left partition, pivot is the new head
        }

        // Find the end of the left partition
        ListNode current = left;
        while (current.next != null) {
            current = current.next;
        }

        // Connect the end of the left partition to the pivot
        current.next = pivot;
        return left; // Return the new head of the sorted list
    }

    // Helper method to partition the list around a pivot value
    public static ListNode[] partition(ListNode head, int pivotValue) {
        ListNode leftHead = null, leftTail = null;
        ListNode rightHead = null, rightTail = null;

        while (head != null) {
            ListNode next = head.next;
            head.next = null; // Unlink current node

            if (head.data < pivotValue) {
                if (leftHead == null) {
                    leftHead = head;
                    leftTail = head;
                } else {
                    leftTail.next = head;
                    leftTail = head;
                }
            } else {
                if (rightHead == null) {
                    rightHead = head;
                    rightTail = head;
                } else {
                    rightTail.next = head;
                    rightTail = head;
                }
            }

            head = next;
        }

        return new ListNode[]{leftHead, rightHead};
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
