# Pigeonhole Sort in Java

## Java Code

```java
import java.util.*;

public class PigeonholeSort {

    // Function to perform pigeonhole sort
    public static void pigeonholeSort(int[] arr) {
        int min = Arrays.stream(arr).min().getAsInt();
        int max = Arrays.stream(arr).max().getAsInt();
        int range = max - min + 1;
        List<Integer>[] holes = new List[range];

        // Initialize empty lists in holes
        for (int i = 0; i < range; i++) {
            holes[i] = new ArrayList<>();
        }

        // Add elements into respective holes
        for (int i = 0; i < arr.length; i++) {
            holes[arr[i] - min].add(arr[i]);
        }

        // Traverse through all holes and put elements back into arr[]
        int index = 0;
        for (int i = 0; i < range; i++) {
            for (Integer num : holes[i]) {
                arr[index++] = num;
            }
        }
    }

    // Main method to test pigeonhole sort
    public static void main(String[] args) {
        int[] arr = {8, 3, 2, 7, 4, 6, 8};
        System.out.println("Original array:");
        for (int num : arr) {
            System.out.print(num + " ");
        }
        System.out.println();

        pigeonholeSort(arr);

        System.out.println("Sorted array:");
        for (int num : arr) {
            System.out.print(num + " ");
        }
    }
}
