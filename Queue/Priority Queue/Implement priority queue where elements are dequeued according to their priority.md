import java.util.PriorityQueue;

class Task implements Comparable<Task> {
    private String name;
    private int priority;

    public Task(String name, int priority) {
        this.name = name;
        this.priority = priority;
    }

    public String getName() {
        return name;
    }

    public int getPriority() {
        return priority;
    }

    @Override
    public int compareTo(Task other) {
        return Integer.compare(this.priority, other.priority);
    }
}

public class CustomPriorityQueueExample {

    public static void main(String[] args) {
        // Create a priority queue of Task objects
        PriorityQueue<Task> priorityQueue = new PriorityQueue<>();

        // Enqueue tasks with their priorities
        priorityQueue.offer(new Task("Task1", 3));
        priorityQueue.offer(new Task("Task2", 1));
        priorityQueue.offer(new Task("Task3", 2));

        // Dequeue tasks according to their priority
        while (!priorityQueue.isEmpty()) {
            Task task = priorityQueue.poll();
            System.out.println("Dequeued: " + task.getName() + " (Priority: " + task.getPriority() + ")");
        }
    }
}
