# 11. Container With Most Water

``` java
public class Main {
    public static int maxArea(int[] height) {
        int l = 0;
        int r = height.length - 1;
        int area = 0;
        while (l < r) {
            area = Math.max(area, Math.min(height[l], height[r]) * (r - l));
            // Change pointer of the smallest one only (to get max area)
            if (height[r] > height[l]) {
                l++;
            } else {
                r--;
            }
        }
        return area;
    }

    public static void main(String[] args) {
//        int[] heights = new int[]{1, 8, 6, 2, 5, 4, 8, 3, 7};
        int[] heights = new int[]{3, 6, 1};
        System.out.println(maxArea(heights));
    }
}
```