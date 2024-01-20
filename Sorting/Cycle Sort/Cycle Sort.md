# Cycle Sort in Java

## Java Code

```java
public class CycleSort {

    // Function to perform cycle sort
    public static void cycleSort(int[] arr) {
        int n = arr.length;

        // Traverse the array to place the correct element at each position
        for (int start = 0; start < n - 1; start++) {
            int item = arr[start];
            int pos = start;

            // Find the correct position for current item
            for (int i = start + 1; i < n; i++) {
                if (arr[i] < item) {
                    pos++;
                }
            }

            // If item is already in correct position, continue
            if (pos == start) {
                continue;
            }

            // Skip duplicates
            while (item == arr[pos]) {
                pos++;
            }

            // Swap the items
            if (pos != start) {
                int temp = item;
                item = arr[pos];
                arr[pos] = temp;
            }

            // Place the current item to its correct position
            while (pos != start) {
                pos = start;
                for (int i = start + 1; i < n; i++) {
                    if (arr[i] < item) {
                        pos++;
                    }
                }

                while (item == arr[pos]) {
                    pos++;
                }

                if (item != arr[pos]) {
                    int temp = item;
                    item = arr[pos];
                    arr[pos] = temp;
                }
            }
        }
    }

    // Main method to test cycle sort
    public static void main(String[] args) {
        int[] arr = {5, 2, 1, 4, 3};
        System.out.println("Original array:");
        for (int num : arr) {
            System.out.print(num + " ");
        }
        System.out.println();

        cycleSort(arr);

        System.out.println("Sorted array:");
        for (int num : arr) {
            System.out.print(num + " ");
        }
    }
}
