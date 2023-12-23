import java.util.ArrayDeque;
import java.util.Deque;

public class SlidingWindowMaximum {

    public static void main(String[] args) {
        int[] nums = {1, 3, -1, -3, 5, 3, 6, 7};
        int k = 3;
        int[] result = maxSlidingWindow(nums, k);
        
        System.out.println("Maximum elements in each sliding window of size " + k + ":");
        for (int num : result) {
            System.out.print(num + " ");
        }
    }

    public static int[] maxSlidingWindow(int[] nums, int k) {
        if (nums == null || nums.length == 0 || k <= 0) {
            return new int[0];
        }

        int n = nums.length;
        int[] result = new int[n - k + 1];
        int ri = 0; // Result index

        Deque<Integer> deque = new ArrayDeque<>();
        
        for (int i = 0; i < nums.length; i++) {
            // Remove elements not within the window
            while (!deque.isEmpty() && deque.peek() < i - k + 1) {
                deque.poll();
            }
            
            // Remove elements from the deque that are less than the current element
            while (!deque.isEmpty() && nums[deque.peekLast()] < nums[i]) {
                deque.pollLast();
            }
            
            // Add current element index to the deque
            deque.offer(i);
            
            // Start adding results only when window size is reached
            if (i >= k - 1) {
                result[ri++] = nums[deque.peek()];
            }
        }
        
        return result;
    }
}
