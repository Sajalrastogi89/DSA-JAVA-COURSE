# Comb Sort in Java

## Java Code

```java
public class CombSort {

    // Function to perform comb sort
    public static void combSort(int[] arr) {
        int n = arr.length;
        int gap = n;
        boolean swapped = true;

        // Keep reducing gap until it becomes 1 and there are no swaps
        while (gap > 1 || swapped) {
            // Update gap value
            gap = getNextGap(gap);

            swapped = false;

            // Compare all elements with current gap
            for (int i = 0; i < n - gap; i++) {
                if (arr[i] > arr[i + gap]) {
                    // Swap arr[i] and arr[i+gap]
                    int temp = arr[i];
                    arr[i] = arr[i + gap];
                    arr[i + gap] = temp;
                    swapped = true;
                }
            }
        }
    }

    // Function to get the next gap value
    public static int getNextGap(int gap) {
        // Shrink gap by shrink factor
        gap = (gap * 10) / 13;
        if (gap < 1) {
            return 1;
        }
        return gap;
    }

    // Main method to test comb sort
    public static void main(String[] args) {
        int[] arr = {8, 4, 1, 56, 3, -44, 23, -6, 28, 0};
        System.out.println("Original array:");
        for (int num : arr) {
            System.out.print(num + " ");
        }
        System.out.println();

        combSort(arr);

        System.out.println("Sorted array:");
        for (int num : arr) {
            System.out.print(num + " ");
        }
    }
}
