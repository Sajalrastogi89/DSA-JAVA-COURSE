import java.util.ArrayDeque;
import java.util.Queue;

public class HotPotatoGame {

    public static void main(String[] args) {
        String[] participants = {"Alice", "Bob", "Charlie", "David", "Eve", "Frank"};
        int numToRemove = 3; // Number of participants to remove in each round

        String winner = playHotPotato(participants, numToRemove);
        System.out.println("Winner: " + winner);
    }

    public static String playHotPotato(String[] participants, int numToRemove) {
        Queue<String> queue = new ArrayDeque<>();

        // Add participants to the queue
        for (String participant : participants) {
            queue.offer(participant);
        }

        // Simulate the elimination process
        while (queue.size() > 1) {
            // Remove participants in a circular manner
            for (int i = 0; i < numToRemove - 1; i++) {
                // Rotate the queue: remove from front and add to end
                queue.offer(queue.poll());
            }
            // Remove the participant at the front of the queue (eliminated)
            System.out.println("Removed: " + queue.poll());
        }

        // Return the winner (last participant remaining)
        return queue.poll();
    }
}
