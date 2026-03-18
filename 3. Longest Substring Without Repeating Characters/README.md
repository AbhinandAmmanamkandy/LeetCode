# 3. Longest Substring Without Repeating Characters

Use two pointers to point left and right
If the character at right is in the ArrayList, pop it from
ArrayList from the first and move the left pointer.

right - left + 1 is used to find length of max substring 

``` java
import java.util.ArrayList;

public class Main {
    public static int lengthOfLongestSubstring(String s) {
        ArrayList<Character> characters = new ArrayList<>();
        int left = 0;
        int right = 0;
        int maxLength = 0;
        while (right < s.length()) {
            while(characters.contains(s.charAt(right))) {
                characters.removeFirst();
                left++;
            }
            characters.add(s.charAt(right));
            maxLength = Math.max(maxLength, right - left + 1);
            right++;
        }
        return maxLength;
    }

    public static void main(String[] args) {
        String s = "abcabcbb";
        System.out.println(lengthOfLongestSubstring(s));
    }
}
```