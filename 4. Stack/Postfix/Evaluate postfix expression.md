import java.util.Stack;

public class EvaluatePostfix {

    // Method to evaluate postfix expression
    public static int evaluate(String postfix) {
        Stack<Integer> stack = new Stack<>();

        for (char ch : postfix.toCharArray()) {
            if (Character.isDigit(ch)) {
                // If character is operand, convert to integer and push onto stack
                stack.push(ch - '0'); // '0' is subtracted to convert char to int
            } else {
                // If character is operator, pop two operands, perform operation, and push result onto stack
                int operand2 = stack.pop();
                int operand1 = stack.pop();
                int result = performOperation(ch, operand1, operand2);
                stack.push(result);
            }
        }

        // Result of postfix expression is on top of the stack
        return stack.pop();
    }

    // Method to perform operation based on operator
    private static int performOperation(char operator, int operand1, int operand2) {
        switch (operator) {
            case '+':
                return operand1 + operand2;
            case '-':
                return operand1 - operand2;
            case '*':
                return operand1 * operand2;
            case '/':
                if (operand2 == 0) {
                    throw new ArithmeticException("Division by zero");
                }
                return operand1 / operand2;
            default:
                throw new IllegalArgumentException("Invalid operator: " + operator);
        }
    }

    public static void main(String[] args) {
        String postfix1 = "23*5+";
        String postfix2 = "46+2/5*7+";

        System.out.println("Postfix expression: " + postfix1);
        System.out.println("Result: " + evaluate(postfix1));

        System.out.println("\nPostfix expression: " + postfix2);
        System.out.println("Result: " + evaluate(postfix2));
    }
}
