# Intersection of Numbers

👓This question is asked by Google. 👓

> Given two integer arrays, return their intersection.
Note: the intersection is the set of elements that are common to both arrays.

Ex: Given the following arrays...

- nums1 = [2, 4, 4, 2], nums2 = [2, 4], return [2, 4]
- nums1 = [1, 2, 3, 3], nums2 = [3, 3], return [3]
- nums1 = [2, 4, 6, 8], nums2 = [1, 3, 5, 7], return []

```java
import java.util.HashSet;
import java.util.Arrays;
import java.util.Set;

public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");

        int[] nums1 = {2, 4, 4, 2};
        int[] nums2 = {2, 4};
        printArray(intersection(nums1, nums2));

        nums1 = new int[]{1, 2, 3, 3};
        nums2 = new int[]{3, 3};
        printArray(intersection(nums1, nums2));

        nums1 = new int[]{2, 4, 6, 8};
        nums2 = new int[]{1, 3, 5, 7};
        printArray(intersection(nums1, nums2));
    }

    public static int[] intersection(int[] nums1, int[] nums2) {
        Set<Integer> set1 = new HashSet<>();
        for (int num : nums1) {
            set1.add(num);
        }

        int[] result = new int[Math.min(nums1.length, nums2.length)];
        int index = 0;

        for (int num : nums2) {
            if (set1.remove(num)) {
                result[index++] = num;
            }
        }

        return Arrays.copyOf(result, index);
    }

    public static void printArray(int[] arr) {
        System.out.print("[");
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i]);
            if (i < arr.length - 1) {
                System.out.print(", ");
            }
        }
        System.out.println("]");
    }
}
```
