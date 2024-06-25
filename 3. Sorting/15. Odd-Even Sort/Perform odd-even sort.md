# Odd-Even Sort in Java

## Java Code

```java
public class OddEvenSort {

    // Function to perform odd-even sort
    public static void oddEvenSort(int[] arr) {
        int n = arr.length;
        boolean sorted = false;

        while (!sorted) {
            sorted = true;

            // Perform odd-even sort on odd indexed elements
            for (int i = 1; i <= n - 2; i += 2) {
                if (arr[i] > arr[i + 1]) {
                    int temp = arr[i];
                    arr[i] = arr[i + 1];
                    arr[i + 1] = temp;
                    sorted = false;
                }
            }

            // Perform odd-even sort on even indexed elements
            for (int i = 0; i <= n - 2; i += 2) {
                if (arr[i] > arr[i + 1]) {
                    int temp = arr[i];
                    arr[i] = arr[i + 1];
                    arr[i + 1] = temp;
                    sorted = false;
                }
            }
        }
    }

    // Main method to test odd-even sort
    public static void main(String[] args) {
        int[] arr = {5, 2, 9, 1, 5, 6};
        System.out.println("Original array:");
        for (int num : arr) {
            System.out.print(num + " ");
        }
        System.out.println();

        oddEvenSort(arr);

        System.out.println("Sorted array:");
        for (int num : arr) {
            System.out.print(num + " ");
        }
    }
}
