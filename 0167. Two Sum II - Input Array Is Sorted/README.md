# Two Sum II - Input Array Is Sorted

## Old way (Two Sum's Way)
``` java
import java.util.Map;
import java.util.Arrays;
import java.util.HashMap;

public class Main {
    public static int[] twoSum(int[] numbers, int target) {
        int diff;
        Map<Integer, Integer> hashMap = new HashMap<>();
        for (int i=0; i<numbers.length; i++) {
            diff = target - numbers[i];
            if (hashMap.containsKey(diff)) {
                // Since 1-Indexed array (add one to it)
                return new int[]{hashMap.get(diff) + 1, i + 1};
            }
            hashMap.put(numbers[i], i);
        }
        return null;
    }

    public static void main(String[] args) {
        int[] numbers = new int[]{2, 7, 11, 15};
        System.out.println(Arrays.toString(twoSum(numbers, 9)));
    }
}
```

## Since it is sorted, we can use two pointers
``` java
import java.util.Arrays;

public class Main {
    public static int[] twoSum(int[] numbers, int target) {
        int l = 0;
        int r = numbers.length - 1;
        int sum;
        while (l < r) {
            sum = numbers[l] + numbers[r];
            if (sum == target) {
                return new int[]{l+1, r+1};
            } else if (sum > target) {
                r--;
            } else {
                l++;
            }
        }
        return null;
    }

    public static void main(String[] args) {
        int[] numbers = new int[]{2, 7, 11, 15};
        System.out.println(Arrays.toString(twoSum(numbers, 9)));
    }
}
```