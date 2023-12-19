import java.util.LinkedList;
import java.util.Queue;

public class QueueExample {

    public static void main(String[] args) {
        // Create a queue using LinkedList (can also use ArrayDeque)
        Queue<Integer> queue = new LinkedList<>();

        // Display the number of elements in the queue
        System.out.println("Number of elements in the queue: " + getSize(queue));

        // Adding elements to the queue
        enqueue(queue, 10);
        enqueue(queue, 20);
        enqueue(queue, 30);

        // Display the number of elements in the queue after adding elements
        System.out.println("Number of elements in the queue: " + getSize(queue));

        // Remove elements to decrease the number of elements in the queue
        dequeue(queue);
        dequeue(queue);

        // Display the number of elements in the queue after removing elements
        System.out.println("Number of elements in the queue: " + getSize(queue));
    }

    // Method to add an element to the queue
    public static void enqueue(Queue<Integer> queue, int element) {
        // Add the element to the rear of the queue
        queue.offer(element);
    }

    // Method to remove an element from the queue
    public static void dequeue(Queue<Integer> queue) {
        // Remove the element from the front of the queue
        Integer removedElement = queue.poll();
        if (removedElement != null) {
            System.out.println("Removed element: " + removedElement);
        } else {
            System.out.println("Queue is empty. Cannot dequeue.");
        }
    }

    // Method to get the number of elements in the queue
    public static int getSize(Queue<Integer> queue) {
        // Return the number of elements in the queue
        return queue.size();
    }
}
