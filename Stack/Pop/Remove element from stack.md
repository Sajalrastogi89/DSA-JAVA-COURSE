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

        // Remove element from the top of the stack
        int removedElement = stack.pop();

        // Print the removed element and the updated stack
        System.out.println("Removed element: " + removedElement);
        System.out.println("Stack after removal: " + stack);
    }
}
