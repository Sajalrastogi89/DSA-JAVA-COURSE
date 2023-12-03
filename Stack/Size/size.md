import java.util.Stack;

public class StackExample {

    public static void main(String[] args) {
        // Create a stack
        Stack<Integer> stack = new Stack<>();

        // Push elements onto the stack
        stack.push(1);
        stack.push(2);
        stack.push(3);

        // Print the size of the stack
        System.out.println("Size of the stack: " + stack.size());

        // Pop an element from the stack
        stack.pop();

        // Print the updated size of the stack
        System.out.println("Size of the stack after popping: " + stack.size());
    }
}
