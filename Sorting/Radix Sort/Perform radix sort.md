# Radix Sort in Java

## Java Code

```java
import java.util.*;

public class RadixSort {

    // Function to find the maximum number in the array
    public static int getMax(int[] arr) {
        int max = arr[0];
        for (int i = 1; i < arr.length; i++) {
            if (arr[i] > max) {
                max = arr[i];
            }
        }
        return max;
    }

    // Function to perform counting sort based on digit at exp
    public static void countingSort(int[] arr, int exp) {
        int n = arr.length;
        int[] output = new int[n]; // output array
        int[] count = new int[10]; // count array for digits 0-9

        // Store count of occurrences in count[]
        for (int i = 0; i < n; i++) {
            count[(arr[i] / exp) % 10]++;
        }

        // Change count[i] so that count[i] now contains actual position of this digit in output[]
        for (int i = 1; i < 10; i++) {
            count[i] += count[i - 1];
        }

        // Build the output array
        for (int i = n - 1; i >= 0; i--) {
            output[count[(arr[i] / exp) % 10] - 1] = arr[i];
            count[(arr[i] / exp) % 10]--;
        }

        // Copy the sorted elements into original array
        for (int i = 0; i < n; i++) {
            arr[i] = output[i];
        }
    }

    // Function to perform radix sort
    public static void radixSort(int[] arr) {
        // Find the maximum number to know number of digits
        int max = getMax(arr);

        // Perform counting sort for every digit. exp is 10^i where i is the current digit number
        for (int exp = 1; max / exp > 0; exp *= 10) {
            countingSort(arr, exp);
        }
    }

    // Main method to test radix sort
    public static void main(String[] args) {
        int[] arr = {170, 45, 75, 90, 802, 24, 2, 66};
        System.out.println("Original array:");
        for (int num : arr) {
            System.out.print(num + " ");
        }
        System.out.println();

        radixSort(arr);

        System.out.println("Sorted array:");
        for (int num : arr) {
            System.out.print(num + " ");
        }
    }
}
