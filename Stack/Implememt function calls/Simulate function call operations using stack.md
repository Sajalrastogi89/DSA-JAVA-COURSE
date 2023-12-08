import java.util.Stack;

public class FunctionCallSimulation {

    // Function to simulate the execution of a function
    public static void simulateFunction(String functionName) {
        System.out.println("Calling function: " + functionName);
        System.out.println("Function " + functionName + " executing...");
        System.out.println("Function " + functionName + " completed.");
    }

    public static void main(String[] args) {
        // Simulate function calls using a stack
        Stack<String> callStack = new Stack<>();

        // Push function calls onto the stack
        callStack.push("function1");
        callStack.push("function2");
        callStack.push("function3");

        // Process each function call until the stack is empty
        while (!callStack.isEmpty()) {
            String function = callStack.pop();
            simulateFunction(function);
        }
    }
}
