class ListNode {
    int data;
    ListNode next;

    ListNode(int data) {
        this.data = data;
        this.next = null;
    }
}

public class DeleteSpecificNodeCircularLinkedList {

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

        // Delete node with data 3
        int dataToDelete = 3;
        head = deleteNode(head, dataToDelete);

        // Print the circular linked list after deletion
        System.out.println("Circular Linked List after deletion of node with data " + dataToDelete + ":");
        printCircularLinkedList(head);
    }

    // Function to delete a specific node with given data from a circular linked list
    public static ListNode deleteNode(ListNode head, int data) {
        if (head == null) {
            System.out.println("Circular linked list is empty. Nothing to delete.");
            return null;
        }

        ListNode current = head;
        ListNode prev = null;

        // Traverse the circular list to find the node with data to delete
        do {
            if (current.data == data) {
                break; // Found the node to delete
            }
            prev = current;
            current = current.next;
        } while (current != head);

        // If node to delete is not found
        if (current == head && current.data != data) {
            System.out.println("Node with data " + data + " not found in the circular linked list.");
            return head; // Return original head
        }

        // If the node to delete is the head node
        if (current == head) {
            ListNode last = head;
            while (last.next != head) {
                last = last.next;
            }
            head = head.next; // Move head to the next node
            last.next = head; // Update last node to skip the deleted node
        } else {
            prev.next = current.next; // Skip the node to delete
        }

        return head; // Return the updated head of the circular linked list
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
