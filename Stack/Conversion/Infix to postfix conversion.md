import java.util.Stack;

public class InfixToPostfix {

    // Method to check if a character is an operator
    private static boolean isOperator(char ch) {
        return ch == '+' || ch == '-' || ch == '*' || ch == '/';
    }

    // Method to get precedence of operators
    private static int precedence(char ch) {
        switch (ch) {
            case '+':
            case '-':
                return 1;
            case '*':
            case '/':
                return 2;
            default:
                return -1;
        }
    }

    // Method to convert infix to postfix expression
    public static String infixToPostfix(String infix) {
        StringBuilder postfix = new StringBuilder();
        Stack<Character> stack = new Stack<>();

        for (char ch : infix.toCharArray()) {
            // If character is operand, add it to postfix
            if (Character.isLetterOrDigit(ch)) {
                postfix.append(ch);
            }
            // If character is '(', push it to stack
            else if (ch == '(') {
                stack.push(ch);
            }
            // If character is ')', pop and append operators from stack until '(' is encountered
            else if (ch == ')') {
                while (!stack.isEmpty() && stack.peek() != '(') {
                    postfix.append(stack.pop());
                }
                stack.pop(); // Pop '(' from stack
            }
            // If character is an operator
            else if (isOperator(ch)) {
                // Pop operators from stack with higher or equal precedence and append to postfix
                while (!stack.isEmpty() && precedence(ch) <= precedence(stack.peek())) {
                    postfix.append(stack.pop());
                }
                // Push current operator onto stack
                stack.push(ch);
            }
        }

        // Pop remaining operators from stack and append to postfix
        while (!stack.isEmpty()) {
            postfix.append(stack.pop());
        }

        return postfix.toString();
    }

    public static void main(String[] args) {
        String infix1 = "a+b*c";
        String infix2 = "(a+b)*c";
        String infix3 = "a*(b+c*d)-e";

        System.out.println("Infix expression: " + infix1);
        System.out.println("Postfix expression: " + infixToPostfix(infix1));

        System.out.println("\nInfix expression: " + infix2);
        System.out.println("Postfix expression: " + infixToPostfix(infix2));

        System.out.println("\nInfix expression: " + infix3);
        System.out.println("Postfix expression: " + infixToPostfix(infix3));
    }
}
