# Ternary Search in Java

## Java Code

```java
public class TernarySearch {

    // Function to perform ternary search
    public static int ternarySearch(int l, int r, int key, int[] arr) {
        if (r >= l) {
            // Calculate mid1 and mid2
            int mid1 = l + (r - l) / 3;
            int mid2 = r - (r - l) / 3;

            // Check if key is present at mid1 or mid2
            if (arr[mid1] == key) {
                return mid1;
            }
            if (arr[mid2] == key) {
                return mid2;
            }

            // Key lies in the left one-third
            if (key < arr[mid1]) {
                return ternarySearch(l, mid1 - 1, key, arr);
            }
            // Key lies in the right one-third
            else if (key > arr[mid2]) {
                return ternarySearch(mid2 + 1, r, key, arr);
            }
            // Key lies in the middle one-third
            else {
                return ternarySearch(mid1 + 1, mid2 - 1, key, arr);
            }
        }

        // Key not found
        return -1;
    }

    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
        int l = 0;
        int r = arr.length - 1;
        int key = 5;

        int result = ternarySearch(l, r, key, arr);

        if (result != -1) {
            System.out.println("Element found at index " + result);
        } else {
            System.out.println("Element not found in the array");
        }
    }
}
