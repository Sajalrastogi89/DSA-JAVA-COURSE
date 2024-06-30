```java
class ListNode {
    int data;
    ListNode next;

    ListNode(int data) {
        this.data = data;
        this.next = null;
    }
}

public class InsertionLinkedList {
    public static void main(String[] args) {
        // Create main linked list: 1 -> 2 -> 3 -> 7 -> 8
        ListNode mainList = new ListNode(1);
        mainList.next = new ListNode(2);
        mainList.next.next = new ListNode(3);
        ListNode mainInsertionPoint = mainList.next.next; // Insert after node with data 3
        mainInsertionPoint.next = new ListNode(7);
        mainInsertionPoint.next.next = new ListNode(8);

        // Create linked list to be inserted: 4 -> 5 -> 6
        ListNode listToInsert = new ListNode(4);
        listToInsert.next = new ListNode(5);
        listToInsert.next.next = new ListNode(6);

        // Print the main list before insertion
        System.out.println("Main Linked List before insertion:");
        printLinkedList(mainList);

        // Perform insertion of listToInsert into mainList after mainInsertionPoint
        insertLinkedList(mainList, mainInsertionPoint, listToInsert);

        // Print the main list after insertion
        System.out.println("\nMain Linked List after insertion:");
        printLinkedList(mainList);
    }

    // Method to insert one linked list into another at a specified position
    public static void insertLinkedList(ListNode mainList, ListNode insertionPoint, ListNode listToInsert) {
        if (mainList == null || insertionPoint == null || listToInsert == null) {
            return; // Handle edge cases where lists or insertion points are null
        }

        ListNode temp = insertionPoint.next; // Store the rest of the main list
        insertionPoint.next = listToInsert; // Connect insertion point to listToInsert

        // Find the end of listToInsert
        ListNode endOfListToInsert = listToInsert;
        while (endOfListToInsert.next != null) {
            endOfListToInsert = endOfListToInsert.next;
        }

        // Connect the end of listToInsert to the rest of the main list
        endOfListToInsert.next = temp;
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
