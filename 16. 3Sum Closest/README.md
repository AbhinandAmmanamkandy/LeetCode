# 16. 3Sum Closest

``` java
import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        int[] nums = {0,1,2};
        int target = 0;
        System.out.println(threeSumClosest(nums, target));
    }

    public static int threeSumClosest(int[] nums, int target) {
        int[] num = Arrays.stream(nums).sorted().toArray();
        int closest = num[0] + num[1] + num[nums.length - 1];
        int i = 0;
        int left;
        int right;
        while (i < num.length) {
            left = i + 1;
            right = num.length - 1;
            while (left < right) {
                int total = num[i] + num[left] + num[right];
                if (Math.abs(total - target) < Math.abs(closest - target)) {
                    closest = total;
                }
                if (total == target) {
                    left++;
                    right--;
                } else if (total < target) {
                    left++;
                } else {
                    right--;
                }
            }
            i++;
        }
        return closest;
    }

}
```