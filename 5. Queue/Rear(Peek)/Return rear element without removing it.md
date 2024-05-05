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

        // Get and display the rear element without removing it
        Integer rearElement = getRearElement(queue);
        if (rearElement != null) {
            System.out.println("Rear element of the queue: " + rearElement);
        } else {
            System.out.println("Queue is empty. No rear element.");
        }

        // Display the queue again
        System.out.println("Queue after peek rear operation: " + queue);
    }

    // Method to add an element to the queue
    public static void enqueue(Queue<Integer> queue, int element) {
        // Add the element to the rear of the queue
        queue.offer(element);
    }

    // Method to get the rear element of the queue without removing it
    public static Integer getRearElement(Queue<Integer> queue) {
        // Convert Queue to LinkedList to access last element
        LinkedList<Integer> list = (LinkedList<Integer>) queue;
        if (!list.isEmpty()) {
            return list.getLast();
        }
        return null;
    }
}
