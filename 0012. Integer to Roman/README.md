# 12. Integer to Roman

``` java
public class Main {
    public static String intToRoman(int num) {
        StringBuilder out = new StringBuilder();
        while (num > 0) {
            if (num >= 1000) {
                num -= 1000;
                out.append("M");
            } else if (num >= 900) {
                num -= 900;
                out.append("CM");
            } else if (num >= 500) {
                num -= 500;
                out.append("D");
            } else if (num >= 400) {
                num -= 400;
                out.append("CD");
            } else if(num >= 100) {
                num -= 100;
                out.append("C");
            } else if (num >= 90) {
                num -= 90;
                out.append("XC");
            } else if (num >= 50) {
                num -= 50;
                out.append("L");
            } else if (num >= 40) {
                num -= 40;
                out.append("XL");
            } else if (num >= 10) {
                num -= 10;
                out.append("X");
            } else if (num == 9) {
                num -= 9;
                out.append("IX");
            } else if (num >= 5) {
                num -= 5;
                out.append("V");
            } else if (num == 4) {
                num -= 4;
                out.append("IV");
            } else {
                num -= 1;
                out.append("I");
            }
        }
        return out.toString();
    }

    public static void main(String[] args) {
        System.out.println(intToRoman(3749));
    }
}
```