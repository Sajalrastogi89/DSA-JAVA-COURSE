import java.util.Stack;

public class SimulateRecursiveWithStack {

    // Method to calculate factorial iteratively using a stack
    public static long factorial(int n) {
        if (n < 0) {
            throw new IllegalArgumentException("Factorial is not defined for negative numbers");
        }

        // Stack to simulate function calls
        Stack<Integer> stack = new Stack<>();
        stack.push(n);
        long result = 1;

        while (!stack.isEmpty()) {
            int current = stack.pop();

            if (current > 1) {
                stack.push(current - 1); // Simulate recursive call with n-1
                stack.push(current);     // Push current value to compute factorial later
            } else {
                result *= current; // Base case: factorial(1) = 1
            }
        }

        return result;
    }

    public static void main(String[] args) {
        int n = 5;
        long factorialValue = factorial(n);
        System.out.println("Factorial of " + n + " is: " + factorialValue);
    }
}
