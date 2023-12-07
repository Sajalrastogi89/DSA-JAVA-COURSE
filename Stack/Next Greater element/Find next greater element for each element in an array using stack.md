import java.util.*;

public class NextGreaterElement {

    public static int[] nextGreaterElements(int[] nums) {
        int n = nums.length;
        int[] result = new int[n];
        Arrays.fill(result, -1); // Initialize result array with -1

        Stack<Integer> stack = new Stack<>();
        
        // Traverse the array
        for (int i = 0; i < n; i++) {
            // Keep popping elements from stack which are less than current element
            while (!stack.isEmpty() && nums[stack.peek()] < nums[i]) {
                result[stack.pop()] = nums[i]; // Current element is the next greater element for popped elements
            }
            stack.push(i); // Push current index onto stack
        }
        
        // For elements remaining in stack, there is no greater element to the right
        while (!stack.isEmpty()) {
            result[stack.pop()] = -1;
        }

        return result;
    }

    public static void main(String[] args) {
        int[] nums = {4, 2, 8, 6, 1, 5, 9};
        
        System.out.println("Original Array: " + Arrays.toString(nums));
        int[] nge = nextGreaterElements(nums);
        System.out.println("Next Greater Elements: " + Arrays.toString(nge));
    }
}
