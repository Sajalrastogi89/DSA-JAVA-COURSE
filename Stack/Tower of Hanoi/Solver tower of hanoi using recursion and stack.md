import java.util.Stack;

public class TowerOfHanoi {

    // Recursive method to solve Tower of Hanoi
    public static void solveTowerOfHanoiRecursive(int n, char source, char auxiliary, char destination) {
        if (n == 1) {
            System.out.println("Move disk 1 from " + source + " to " + destination);
            return;
        }
        solveTowerOfHanoiRecursive(n - 1, source, destination, auxiliary);
        System.out.println("Move disk " + n + " from " + source + " to " + destination);
        solveTowerOfHanoiRecursive(n - 1, auxiliary, source, destination);
    }

    // Stack-based method to simulate Tower of Hanoi
    public static void solveTowerOfHanoiStack(int n, char source, char auxiliary, char destination) {
        Stack<Operation> stack = new Stack<>();
        stack.push(new Operation(n, source, auxiliary, destination));

        while (!stack.isEmpty()) {
            Operation current = stack.pop();

            if (current.n == 1) {
                System.out.println("Move disk 1 from " + current.source + " to " + current.destination);
            } else {
                stack.push(new Operation(current.n - 1, current.auxiliary, current.source, current.destination));
                stack.push(new Operation(1, current.source, current.auxiliary, current.destination));
                stack.push(new Operation(current.n - 1, current.source, current.destination, current.auxiliary));
            }
        }
    }

    // Helper class to represent operations in stack-based approach
    static class Operation {
        int n;
        char source, auxiliary, destination;

        public Operation(int n, char source, char auxiliary, char destination) {
            this.n = n;
            this.source = source;
            this.auxiliary = auxiliary;
            this.destination = destination;
        }
    }

    public static void main(String[] args) {
        int n = 3; // Number of disks
        char source = 'A', auxiliary = 'B', destination = 'C';

        System.out.println("Recursive Solution:");
        solveTowerOfHanoiRecursive(n, source, auxiliary, destination);

        System.out.println("\nStack-based Solution:");
        solveTowerOfHanoiStack(n, source, auxiliary, destination);
    }
}
