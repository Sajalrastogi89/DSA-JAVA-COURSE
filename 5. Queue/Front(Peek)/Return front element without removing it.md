import java.util.LinkedList;
import java.util.Queue;

public class QueueExample {

    public static void main(String[] args) {
        // Create a queue using LinkedList (can also use ArrayDeque)
        Queue<Integer> queue = new LinkedList<>();

        // Adding elements to the queue
        enqueue(queue, 10);
        enqueue(queue, 20);
        enqueue(queue, 30);

        // Display the queue
        System.out.println("Queue after enqueuing elements: " + queue);

        // Get and display the front element without removing it
        Integer frontElement = peek(queue);
        if (frontElement != null) {
            System.out.println("Front element of the queue: " + frontElement);
        } else {
            System.out.println("Queue is empty. No front element.");
        }

        // Display the queue again
        System.out.println("Queue after peek operation: " + queue);
    }

    // Method to add an element to the queue
    public static void enqueue(Queue<Integer> queue, int element) {
        // Add the element to the rear of the queue
        queue.offer(element);
    }

    // Method to get the front element of the queue without removing it
    public static Integer peek(Queue<Integer> queue) {
        // Return the front element of the queue
        return queue.peek();
    }
}
