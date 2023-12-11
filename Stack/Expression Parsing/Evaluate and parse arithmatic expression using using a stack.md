import java.util.*;

public class EvaluateArithmeticExpression {

    // Method to evaluate arithmetic expression
    public static double evaluateExpression(String expression) {
        // Convert infix expression to postfix
        String postfix = infixToPostfix(expression);

        // Evaluate postfix expression
        return evaluatePostfix(postfix);
    }

    // Method to convert infix expression to postfix using Shunting Yard algorithm
    private static String infixToPostfix(String expression) {
        StringBuilder result = new StringBuilder();
        Stack<Character> stack = new Stack<>();

        for (int i = 0; i < expression.length(); i++) {
            char c = expression.charAt(i);

            if (Character.isDigit(c) || c == '.') {
                // Append operands directly to result
                result.append(c);
            } else if (c == '(') {
                // Push opening parenthesis onto stack
                stack.push(c);
            } else if (c == ')') {
                // Pop and append all operators until matching '(' is found
                while (!stack.isEmpty() && stack.peek() != '(') {
                    result.append(stack.pop());
                }
                stack.pop(); // Remove '(' from stack
            } else {
                // Operator encountered
                while (!stack.isEmpty() && precedence(stack.peek()) >= precedence(c)) {
                    result.append(stack.pop());
                }
                stack.push(c);
            }
        }

        // Pop remaining operators from stack
        while (!stack.isEmpty()) {
            result.append(stack.pop());
        }

        return result.toString();
    }

    // Method to evaluate postfix expression
    private static double evaluatePostfix(String postfix) {
        Stack<Double> stack = new Stack<>();
        String[] tokens = postfix.split("\\s+");

        for (String token : tokens) {
            if (isNumeric(token)) {
                stack.push(Double.parseDouble(token));
            } else {
                double operand2 = stack.pop();
                double operand1 = stack.pop();
                double result = performOperation(token.charAt(0), operand1, operand2);
                stack.push(result);
            }
        }

        return stack.pop();
    }

    // Helper method to determine operator precedence
    private static int precedence(char operator) {
        switch (operator) {
            case '+':
            case '-':
                return 1;
            case '*':
            case '/':
                return 2;
            default:
                return 0;
        }
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

    // Helper method to perform arithmetic operations
    private static double performOperation(char operator, double operand1, double operand2) {
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
        String expression1 = "3 + 4 * 5";
        String expression2 = "(6 - 2) / 2 + 5 * 2";
        
        System.out.println("Expression: " + expression1);
        double result1 = evaluateExpression(expression1);
        System.out.println("Result: " + result1);

        System.out.println("\nExpression: " + expression2);
        double result2 = evaluateExpression(expression2);
        System.out.println("Result: " + result2);
    }
}
