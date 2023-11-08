import java.util.HashSet;

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

public class RemoveDuplicatesDoublyLinkedList {
    public static void main(String[] args) {
        // Create a sample doubly linked list: 1 <-> 2 <-> 2 <-> 3 <-> 3 <-> 4
        DoublyListNode head = new DoublyListNode(1);
        DoublyListNode node2 = new DoublyListNode(2);
        DoublyListNode node3 = new DoublyListNode(2);
        DoublyListNode node4 = new DoublyListNode(3);
        DoublyListNode node5 = new DoublyListNode(3);
        DoublyListNode node6 = new DoublyListNode(4);

        head.next = node2;
        node2.prev = head;
        node2.next = node3;
        node3.prev = node2;
        node3.next = node4;
        node4.prev = node3;
        node4.next = node5;
        node5.prev = node4;
        node5.next = node6;
        node6.prev = node5;

        System.out.println("Original Doubly Linked List:");
        printDoublyLinkedList(head);

        DoublyListNode uniqueList = removeDuplicates(head);

        System.out.println("\nDoubly Linked List after removing duplicates:");
        printDoublyLinkedList(uniqueList);
    }

    // Function to remove duplicates from a doubly linked list
    public static DoublyListNode removeDuplicates(DoublyListNode head) {
        if (head == null || head.next == null) {
            return head;
        }

        HashSet<Integer> seen = new HashSet<>();
        DoublyListNode current = head;
        seen.add(current.data);

        while (current != null) {
            if (current.next != null && seen.contains(current.next.data)) {
                // Skip the duplicate node
                current.next = current.next.next;
                if (current.next != null) {
                    current.next.prev = current;
                }
            } else {
                seen.add(current.data);
                current = current.next;
            }
        }

        return head;
    }

    // Utility function to print the doubly linked list
    public static void printDoublyLinkedList(DoublyListNode head) {
        DoublyListNode current = head;
        while (current != null) {
            System.out.print(current.data + " <-> ");
            current = current.next;
        }
        System.out.println("null");
    }
}
