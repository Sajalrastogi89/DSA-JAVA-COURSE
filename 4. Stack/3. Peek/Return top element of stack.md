import java.util.Stack;

public class StackExample {

    public static void main(String[] args) {
        // Create a stack
        Stack<Integer> stack = new Stack<>();

        // Push elements onto the stack
        stack.push(1);
        stack.push(2);
        stack.push(3);

        // Print the stack
        System.out.println("Initial stack: " + stack);

        // Return the top element of the stack
        int topElement = stack.peek();

        // Print the top element
        System.out.println("Top element of the stack: " + topElement);
    }
}
