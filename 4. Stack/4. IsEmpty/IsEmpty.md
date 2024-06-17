import java.util.Stack;

public class StackExample {

    public static void main(String[] args) {
        // Create a stack
        Stack<Integer> stack = new Stack<>();

        // Check if the stack is empty
        System.out.println("Is stack empty? " + stack.isEmpty());

        // Push elements onto the stack
        stack.push(1);
        stack.push(2);
        stack.push(3);

        // Check again after pushing elements
        System.out.println("Is stack empty after pushing? " + stack.isEmpty());

        // Pop all elements from the stack
        while (!stack.isEmpty()) {
            stack.pop();
        }

        // Check again after popping all elements
        System.out.println("Is stack empty after popping? " + stack.isEmpty());
    }
}
