import java.util.LinkedList;
import java.util.Queue;

public class QueueExample {

    public static void main(String[] args) {
        // Create a queue using LinkedList (can also use ArrayDeque)
        Queue<Integer> queue = new LinkedList<>();

        // Display if the queue is empty or not
        System.out.println("Is the queue empty? " + isEmpty(queue));

        // Adding elements to the queue
        enqueue(queue, 10);
        enqueue(queue, 20);
        enqueue(queue, 30);

        // Display if the queue is empty after adding elements
        System.out.println("Is the queue empty? " + isEmpty(queue));

        // Remove elements to make the queue empty
        dequeue(queue);
        dequeue(queue);
        dequeue(queue);

        // Display if the queue is empty after removing elements
        System.out.println("Is the queue empty? " + isEmpty(queue));
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

    // Method to check if the queue is empty
    public static boolean isEmpty(Queue<Integer> queue) {
        // Check if the queue contains no elements
        return queue.isEmpty();
    }
}
