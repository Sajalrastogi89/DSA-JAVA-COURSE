class DoublyListNode {
    int data;
    DoublyListNode prev;
    DoublyListNode next;

    DoublyListNode(int data) {
        this.data = data;
        this.prev = null;
        this.next = null;
    }
}

public class BinarySearchSortedDoublyLinkedList {
    public static void main(String[] args) {
        // Create a sample sorted doubly linked list: 1 <-> 2 <-> 3 <-> 4 <-> 5
        DoublyListNode head = new DoublyListNode(1);
        DoublyListNode node2 = new DoublyListNode(2);
        DoublyListNode node3 = new DoublyListNode(3);
        DoublyListNode node4 = new DoublyListNode(4);
        DoublyListNode node5 = new DoublyListNode(5);

        head.next = node2;
        node2.prev = head;
        node2.next = node3;
        node3.prev = node2;
        node3.next = node4;
        node4.prev = node3;
        node4.next = node5;
        node5.prev = node4;

        int target = 3;
        DoublyListNode result = binarySearch(head, target);

        if (result != null) {
            System.out.println("Node with data " + target + " found.");
        } else {
            System.out.println("Node with data " + target + " not found.");
        }
    }

    // Function to perform binary search in a sorted doubly linked list
    public static DoublyListNode binarySearch(DoublyListNode head, int target) {
        DoublyListNode left = head;
        DoublyListNode right = findEnd(head);

        while (left != null && right != null && left != right && left.prev != right) {
            DoublyListNode mid = getMid(left, right);

            if (mid.data == target) {
                return mid;
            } else if (mid.data < target) {
                left = mid.next;
            } else {
                right = mid.prev;
            }
        }

        if (left != null && left.data == target) {
            return left;
        }

        return null;
    }

    // Function to find the end node of the doubly linked list
    private static DoublyListNode findEnd(DoublyListNode head) {
        DoublyListNode current = head;
        while (current != null && current.next != null) {
            current = current.next;
        }
        return current;
    }

    // Function to find the middle node between two nodes in the doubly linked list
    private static DoublyListNode getMid(DoublyListNode left, DoublyListNode right) {
        DoublyListNode slow = left;
        DoublyListNode fast = left;

        while (fast != right && fast != null && fast.next != right) {
            slow = slow.next;
            fast = fast.next.next;
        }

        return slow;
    }
}
