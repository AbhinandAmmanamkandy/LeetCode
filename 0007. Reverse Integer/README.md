# 7. Reverse Integer

If current value is greater than Integer.MAX_VALUE - digit / 10
Here divide by 10 is to make sure that in next line it multiplies it 
by 10 and adds it by digit overflows it

``` java
public class Main {
    public static int reverse(int x) {
        boolean isNegative = false;
        if (x < 0) {
            isNegative = true;
            x = -x;
        }
        int temp = 0;
        while (x > 0) {
            int digit = x % 10;
            x /= 10;
            if (temp > (Integer.MAX_VALUE - digit) / 10) {
                return 0;
            }
            temp = (temp * 10) + digit;
        }
        return isNegative ? -temp : temp;
    }
    public static void main(String[] args) {
        int x = -123;
        System.out.println(reverse(x));
    }
}
```