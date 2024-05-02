public class JumpSearch {

    // Method to perform Jump Search
    public static int jumpSearch(int[] array, int target) {
        int n = array.length;
        int step = (int) Math.sqrt(n); // Calculate the jump step

        int prev = 0; // Starting index of the block

        // Jump through the blocks until the end of the array or the element is greater than the target
        while (array[Math.min(step, n) - 1] < target) {
            prev = step; // Move to the next block
            step += (int) Math.sqrt(n); // Update step

            // If we've moved past the array bounds, the element is not present
            if (prev >= n) {
                return -1;
            }
        }

        // Perform linear search within the block
        while (array[prev] < target) {
            prev++;
            
            // If we reached the next block or end of the array
            if (prev == Math.min(step, n)) {
                return -1;
            }
        }

        // Check if the element is found
        if (array[prev] == target) {
            return prev;
        }

        // Element not found
        return -1;
    }

    // Driver method to test Jump Search
    public static void main(String[] args) {
        int[] array = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 12, 14, 18, 19};
        int target = 14;

        int index = jumpSearch(array, target);

        if (index != -1) {
            System.out.println("Element " + target + " found at index: " + index);
        } else {
            System.out.println("Element " + target + " not found in the array.");
        }
    }
}
