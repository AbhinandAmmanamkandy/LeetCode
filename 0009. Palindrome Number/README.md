# 9. Palindrome Number

``` java
public class Main {
    public static boolean isPalindrome(int x) {
        int temp = x;
        int reversed = 0;
        while (temp > 0) {
            reversed *= 10;
            reversed += temp % 10;
            temp /= 10;
        }
        return reversed == x;
    }
    public static void main(String[] args) {
        System.out.println(isPalindrome(-121));
    }
}
```