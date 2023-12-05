import java.util.Stack;

public class BalancedExpression {

    public static boolean isBalanced(String expression) {
        Stack<Character> stack = new Stack<>();

        for (char ch : expression.toCharArray()) {
            if (ch == '(' || ch == '{' || ch == '[') {
                stack.push(ch);
            } else if (ch == ')' || ch == '}' || ch == ']') {
                if (stack.isEmpty()) {
                    return false; // Closing bracket with no matching opening bracket
                }
                char top = stack.pop();
                if ((ch == ')' && top != '(') || (ch == '}' && top != '{') || (ch == ']' && top != '[')) {
                    return false; // Mismatched brackets
                }
            }
        }

        return stack.isEmpty(); // Stack should be empty for balanced expression
    }

    public static void main(String[] args) {
        String expression1 = "{[()]()}";
        String expression2 = "{[(])}";
        String expression3 = "{[}";

        System.out.println("Expression 1 is balanced: " + isBalanced(expression1)); // true
        System.out.println("Expression 2 is balanced: " + isBalanced(expression2)); // false
        System.out.println("Expression 3 is balanced: " + isBalanced(expression3)); // false
    }
}
