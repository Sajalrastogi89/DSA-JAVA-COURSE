import java.util.ArrayDeque;
import java.util.Queue;

public class TaskScheduler {

    private Queue<Runnable> taskQueue;

    public TaskScheduler() {
        // Initialize a queue to store tasks
        taskQueue = new ArrayDeque<>();
    }

    public void addTask(Runnable task) {
        // Add task to the end of the queue
        taskQueue.offer(task);
    }

    public void runTasks() {
        // Process tasks in the order they were added
        while (!taskQueue.isEmpty()) {
            Runnable task = taskQueue.poll();
            task.run();
        }
    }

    public static void main(String[] args) {
        TaskScheduler scheduler = new TaskScheduler();

        // Adding tasks to the scheduler with specific order
        scheduler.addTask(() -> System.out.println("Task 1 executed"));
        scheduler.addTask(() -> System.out.println("Task 2 executed"));
        scheduler.addTask(() -> System.out.println("Task 3 executed"));
        scheduler.addTask(() -> System.out.println("Task 4 executed"));

        // Run tasks in the added order
        scheduler.runTasks();
    }
}
