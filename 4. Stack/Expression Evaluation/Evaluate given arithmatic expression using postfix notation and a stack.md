import java.util.*;

public class EvaluatePostfixExpression {

    // Method to evaluate postfix expression
    public static double evaluatePostfix(String postfix) {
        Stack<Double> stack = new Stack<>();

        // Split the postfix expression into tokens
        String[] tokens = postfix.split("\\s+");

        for (String token : tokens) {
            if (isNumeric(token)) {
                // If token is numeric, push onto stack
                stack.push(Double.parseDouble(token));
            } else if (isOperator(token)) {
                // If token is operator, pop operands from stack, perform operation, and push result back
                double operand2 = stack.pop();
                double operand1 = stack.pop();
                double result = performOperation(token, operand1, operand2);
                stack.push(result);
            } else {
                throw new IllegalArgumentException("Invalid token: " + token);
            }
        }

        // Final result is on top of stack
        return stack.pop();
    }

    // Helper method to check if token is numeric
    private static boolean isNumeric(String token) {
        try {
            Double.parseDouble(token);
            return true;
        } catch (NumberFormatException e) {
            return false;
        }
    }

    // Helper method to check if token is operator
    private static boolean isOperator(String token) {
        return token.equals("+") || token.equals("-") || token.equals("*") || token.equals("/");
    }

    // Helper method to perform arithmetic operation based on operator
    private static double performOperation(String operator, double operand1, double operand2) {
        switch (operator) {
            case "+":
                return operand1 + operand2;
            case "-":
                return operand1 - operand2;
            case "*":
                return operand1 * operand2;
            case "/":
                if (operand2 == 0) {
                    throw new ArithmeticException("Division by zero");
                }
                return operand1 / operand2;
            default:
                throw new IllegalArgumentException("Invalid operator: " + operator);
        }
    }

    public static void main(String[] args) {
        String postfixExpression1 = "3 4 + 5 *";
        String postfixExpression2 = "6 2 / 5 *";

        System.out.println("Postfix expression: " + postfixExpression1);
        double result1 = evaluatePostfix(postfixExpression1);
        System.out.println("Result: " + result1);

        System.out.println("\nPostfix expression: " + postfixExpression2);
        double result2 = evaluatePostfix(postfixExpression2);
        System.out.println("Result: " + result2);
    }
}
