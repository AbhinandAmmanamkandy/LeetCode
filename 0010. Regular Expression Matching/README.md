# 10. Regular Expression Matching

``` java
public class Main {
    // For null checking
    enum Result {
        TRUE, FALSE
    }
    
    public boolean isMatch(String s, String p) {
        Result[][] memo = new Result[s.length() + 1][p.length() + 1];
        return isMatch(0, 0, s, p, memo);
    }


    public boolean isMatch(int sIndex, int pIndex, String s, String p, Result[][] memo) {
        // Memoization
        if (memo[sIndex][pIndex] != null) {
            return memo[sIndex][pIndex] == Result.TRUE;
        }
        boolean matched;
        // If pattern is finished, return string is finished or not
        if (pIndex == p.length()) {
            matched = sIndex == s.length();
        } else {
            // Check currect character matches with pattern character or is '.'
            boolean firstMatch = (sIndex < s.length() &&
                                    (p.charAt(pIndex) == s.charAt(sIndex) ||
                                    p.charAt(pIndex) == '.'));
            // If '*' is found in next character
            if (pIndex+1 < p.length() && p.charAt(pIndex+1) == '*') {
                // Ignore it ie 0 or more case
                // Or use it by checking next character is same or not 
                // by incrementing string index only
                matched = isMatch(sIndex,pIndex+2, s, p, memo) || 
                            (firstMatch && isMatch(sIndex+1, pIndex,s, p, memo));
            } else {
                // Check next characeter
                matched = firstMatch && isMatch(sIndex+1, pIndex+1, s, p, memo);
            }
        }
        memo[sIndex][pIndex] = matched ? Result.TRUE : Result.FALSE;
        return matched;
    }
}
```