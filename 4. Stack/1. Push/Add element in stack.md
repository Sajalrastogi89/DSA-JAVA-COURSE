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
        System.out.println("Stack after initial push operations: " + stack);

        // Add element at the top of the stack
        int elementToAdd = 4;
        stack.push(elementToAdd);

        // Print the stack after adding element
        System.out.println("Stack after adding " + elementToAdd + ": " + stack);
    }
}
