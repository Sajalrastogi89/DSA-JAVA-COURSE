# Tim Sort in Java

Tim Sort is a hybrid sorting algorithm derived from merge sort and insertion sort, designed to perform well on many kinds of real-world data. It is the default sorting algorithm in Python's `sorted()` function and Java's `Arrays.sort()` method.

Java Code:

```java
import java.util.*;

public class TimSort {

    // Function to perform insertion sort
    public static void insertionSort(int[] arr, int left, int right) {
        for (int i = left + 1; i <= right; i++) {
            int temp = arr[i];
            int j = i - 1;
            while (j >= left && arr[j] > temp) {
                arr[j + 1] = arr[j];
                j--;
            }
            arr[j + 1] = temp;
        }
    }

    // Function to perform merge operation
    public static void merge(int[] arr, int l, int m, int r) {
        // Original array is divided into two parts
        int len1 = m - l + 1, len2 = r - m;
        int[] left = new int[len1];
        int[] right = new int[len2];
        for (int x = 0; x < len1; x++)
            left[x] = arr[l + x];
        for (int x = 0; x < len2; x++)
            right[x] = arr[m + 1 + x];

        int i = 0;
        int j = 0;
        int k = l;

        // Merging the arrays
        while (i < len1 && j < len2) {
            if (left[i] <= right[j]) {
                arr[k] = left[i];
                i++;
            } else {
                arr[k] = right[j];
                j++;
            }
            k++;
        }

        // Copy remaining elements of left[] if any
        while (i < len1) {
            arr[k] = left[i];
            k++;
            i++;
        }

        // Copy remaining elements of right[] if any
        while (j < len2) {
            arr[k] = right[j];
            k++;
            j++;
        }
    }

    // Function to perform tim sort
    public static void timSort(int[] arr) {
        int n = arr.length;
        int minRun = 32;

        // Performing insertion sort for each run
        for (int i = 0; i < n; i += minRun) {
            insertionSort(arr, i, Math.min((i + minRun - 1), (n - 1)));
        }

        // Merging the runs
        for (int size = minRun; size < n; size = 2 * size) {
            for (int left = 0; left < n; left += 2 * size) {
                int mid = left + size - 1;
                int right = Math.min((left + 2 * size - 1), (n - 1));
                merge(arr, left, mid, right);
            }
        }
    }

    // Main method to test tim sort
    public static void main(String[] args) {
        int[] arr = {5, 21, 7, 23, 19, 34, 2, 12};
        System.out.println("Original array:");
        for (int num : arr) {
            System.out.print(num + " ");
        }
        System.out.println();

        timSort(arr);

        System.out.println("Sorted array:");
        for (int num : arr) {
            System.out.print(num + " ");
        }
    }
}
