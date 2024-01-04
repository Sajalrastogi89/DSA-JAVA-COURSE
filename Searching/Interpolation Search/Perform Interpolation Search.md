public class InterpolationSearch {

    // Method to perform Interpolation Search
    public static int interpolationSearch(int[] array, int key) {
        int low = 0;
        int high = array.length - 1;

        while (low <= high && key >= array[low] && key <= array[high]) {
            if (low == high) {
                if (array[low] == key) {
                    return low;
                }
                return -1;
            }

            // Estimate the position using the interpolation formula
            int pos = low + (int) (((double) (high - low) / 
                     (array[high] - array[low])) * (key - array[low]));

            // Check if the key is found
            if (array[pos] == key) {
                return pos;
            }

            // If key is larger, key is in the right subarray
            if (array[pos] < key) {
                low = pos + 1;
            }
            // If key is smaller, key is in the left subarray
            else {
                high = pos - 1;
            }
        }

        return -1; // Key not found
    }

    // Driver method to test Interpolation Search
    public static void main(String[] args) {
        int[] array = {10, 12, 14, 18, 19, 21, 23, 25, 30, 35, 40, 45, 50};
        int key = 18;

        int index = interpolationSearch(array, key);

        if (index != -1) {
            System.out.println("Element " + key + " found at index: " + index);
        } else {
            System.out.println("Element " + key + " not found in the array.");
        }
    }
}
