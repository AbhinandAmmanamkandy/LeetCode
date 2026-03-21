# 8. String to Integer (atoi)

``` java
public class Main {
    public static int myAtoi(String s) {
        if (s.isEmpty())
            return 0;

        int i = 0;
        while (i < s.length() && s.charAt(i) == ' ') {
            i++;
        }
        boolean isNegative = false;
        if (i < s.length() && s.charAt(i) == '-') {
            isNegative = true;
            i++;
        } else if (i < s.length() && s.charAt(i) == '+') {
            i++;
        }
        int out = 0;
        while (i < s.length() && Character.isDigit(s.charAt(i))) {
            int val = Integer.parseInt(s.charAt(i) + "");
            if (out > (Integer.MAX_VALUE - val) / 10) {
                return isNegative ? Integer.MIN_VALUE : Integer.MAX_VALUE;
            }
            out *= 10;
            out += val;
            i++;
        }
        return isNegative ? -out : out;
    }
    public static void main(String[] args) {
        String s = " ";
        System.out.println(myAtoi(s));
    }
}
```