public class LinearSearch {

    public static int linearSearch(int[] arr, int target) {
        // Iterate through each element of the array
        for (int i = 0; i < arr.length; i++) {
            // If the target element is found, return its index
            if (arr[i] == target) {
                return i;
            }
        }
        // If the element is not found, return -1
        return -1;
    }

    public static void main(String[] args) {
        int[] arr = {10, 30, 20, 5, 15};
        int target = 20;

        // Perform linear search on the array
        int index = linearSearch(arr, target);

        if (index != -1) {
            System.out.println("Element " + target + " found at index " + index);
        } else {
            System.out.println("Element " + target + " not found in the array");
        }
    }
}
