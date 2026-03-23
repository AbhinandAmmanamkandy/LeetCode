# 15. 3Sum

``` java
import java.util.*;

public class Main {
    public static List<List<Integer>> threeSum(int[] nums) {
        int l;
        int r;
        int sum;
        int target;
        // Sort it to avoid dupicates
        Arrays.sort(nums);
        List<List<Integer>> out = new ArrayList<>();
        for (int i=0; i<nums.length;i++) {
            if (i > 0 && nums[i] == nums[i - 1]) continue;
            l = i + 1;
            r = nums.length - 1;
            target = -nums[i];
            while (l < r) {
                sum = nums[l] + nums[r];
                if (sum == target) {
                    out.add(new ArrayList<>(Arrays.asList(nums[i], nums[l], nums[r])));
                    l++;
                    r--;
                    // Increased pointer may still be duplicates
                    while (l < r && nums[l] == nums[l - 1]) l++;
                    while (l < r && nums[r] == nums[r + 1]) r--;
                } else if (sum < target) {
                    l++;
                } else {
                    r--;
                }
            }
        }
        return out;
    }

    public static void main(String[] args) {
        int[] nums = new int[]{-100,-70,-60,110,120,130,160};
        System.out.println(threeSum(nums));;
    }
}
```