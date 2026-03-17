# Zigzag Conversion

``` java
public class Main {
    public static String convert(String s, int numRows) {

        StringBuilder out = new StringBuilder();

        int numCols = 0;
        int step = numRows;
        int count = 0;
        while (count < s.length()) {
            count += step;
            step = step == numRows ? step - 2 > 0 ? step - 2 : 1 : numRows;
            numCols++;
        }

        char[][] chars = new char[numRows][numCols];
        int col = 0;
        count = 0;
        int i;
        boolean increment = false;
        while (count < s.length()) {
            for (i = 0; i < numRows && count < s.length(); i++) {
                chars[i][col] = s.charAt(count++);
                increment = true;
            }
            if (increment) {
                col++;
                increment = false;
            }
            for (i = i - 2; i > 0 && count < s.length(); i--) {
                chars[i][col] = s.charAt(count++);
                increment = true;
            }
            if (increment) {
                col++;
                increment = false;
            }
        }

        for (i = 0; i < numRows; i++) {
            for (int j = 0; j < numCols; j++) {
                if (chars[i][j] != '\u0000') {
                    out.append(chars[i][j]);
                }
            }
        }

        return out.toString();
    }

    public static void main(String[] args) {
        String s = "PAYPALISHIRING";
        System.out.println(convert(s, 3));
    }
}
```
