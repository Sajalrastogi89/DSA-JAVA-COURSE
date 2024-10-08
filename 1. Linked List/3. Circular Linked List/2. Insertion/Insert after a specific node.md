```java
class ListNode {
    int data;
    ListNode next;

    ListNode(int data) {
        this.data = data;
        this.next = null;
    }
}

public class InsertAfterSpecificNodeCircularLinkedList {

    public static void main(String[] args) {
        // Create a circular linked list: 1 -> 2 -> 3 -> 4 -> 5
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

        // Insert node with data 10 after node with data 3
        ListNode nodeToInsertAfter = head.next.next; // Node with data 3
        insertAfter(nodeToInsertAfter, 10);

        // Print the circular linked list after insertion
        System.out.println("Circular Linked List after insertion:");
        printCircularLinkedList(head);
    }

    // Function to insert a node after a specific node in a circular linked list
    public static void insertAfter(ListNode prevNode, int newData) {
        if (prevNode == null) {
            System.out.println("Previous node cannot be null.");
            return;
        }

        ListNode newNode = new ListNode(newData);
        newNode.next = prevNode.next;
        prevNode.next = newNode;
    }

    // Function to print a circular linked list
    public static void printCircularLinkedList(ListNode head) {
        if (head == null) {
            System.out.println("Circular linked list is empty.");
            return;
        }

        ListNode current = head;
        do {
            System.out.print(current.data + " -> ");
            current = current.next;
        } while (current != head);

        System.out.println("(head)");
    }
}
