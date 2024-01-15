# Bucket Sort in Java

## Java Code

```java
import java.util.*;

public class BucketSort {

    // Function to perform bucket sort
    public static void bucketSort(float[] arr) {
        int n = arr.length;
        
        // Create bucket list
        List<Float>[] buckets = new List[n];
        for (int i = 0; i < n; i++) {
            buckets[i] = new ArrayList<>();
        }

        // Add elements into the buckets
        for (int i = 0; i < n; i++) {
            int bucketIndex = (int) (n * arr[i]);
            buckets[bucketIndex].add(arr[i]);
        }

        // Sort each bucket
        for (int i = 0; i < n; i++) {
            Collections.sort(buckets[i]);
        }

        // Concatenate all buckets into arr[]
        int index = 0;
        for (int i = 0; i < n; i++) {
            for (float num : buckets[i]) {
                arr[index++] = num;
            }
        }
    }

    // Main method to test bucket sort
    public static void main(String[] args) {
        float[] arr = { (float)0.897, (float)0.565,
                        (float)0.656, (float)0.1234,
                        (float)0.665, (float)0.3434 };
                        
        System.out.println("Original array:");
        for (float num : arr) {
            System.out.print(num + " ");
        }
        System.out.println();

        bucketSort(arr);

        System.out.println("Sorted array:");
        for (float num : arr) {
            System.out.print(num + " ");
        }
    }
}
