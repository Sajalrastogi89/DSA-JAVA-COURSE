```java
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

public class DoublyLinkedListLinearSearch {
    public static void main(String[] args) {
        // Create a sample doubly linked list: 1 <-> 2 <-> 3 <-> 4 <-> 5
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
        DoublyListNode result = linearSearch(head, target);

        if (result != null) {
            System.out.println("Node with data " + target + " found.");
        } else {
            System.out.println("Node with data " + target + " not found.");
        }
    }

    // Function to perform linear search in a doubly linked list
    public static DoublyListNode linearSearch(DoublyListNode head, int target) {
        DoublyListNode current = head;

        // Traverse from head to find the target
        while (current != null) {
            if (current.data == target) {
                return current;
            }
            current = current.next;
        }

        // If target not found, return null
        return null;
    }
}
