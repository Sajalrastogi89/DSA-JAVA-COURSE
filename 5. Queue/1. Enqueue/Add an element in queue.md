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

        // Adding more elements to the queue
        enqueue(queue, 40);
        enqueue(queue, 50);

        // Display the queue again
        System.out.println("Queue after adding more elements: " + queue);
    }

    // Method to add an element to the queue
    public static void enqueue(Queue<Integer> queue, int element) {
        // Add the element to the rear of the queue
        queue.offer(element);
    }
}
