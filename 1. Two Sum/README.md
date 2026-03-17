# Two Sum

``` java
import java.util.Arrays;
import java.util.HashMap;

public class Main {
    public static int[] twoSum(int[] nums, int target) {
        int diff;
        HashMap<Integer, Integer> hashMap = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            diff = target - nums[i];
            if (hashMap.containsKey(diff)) {
                return new int[]{hashMap.get(diff), i};
            }
            hashMap.put(nums[i], i);
        }
        return null;
    }

    public static void main(String[] args) {
        int[] nums = {2,7,11,15};
        int target = 9;
        System.out.println(Arrays.toString(twoSum(nums, target)));
    }
}
```
