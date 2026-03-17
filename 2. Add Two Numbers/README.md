# Add Two Numbers

``` java
public class Main {
    public static class ListNode {
        int val;
        ListNode next;

        ListNode() {
        }

        ListNode(int val) {
            this.val = val;
        }

        ListNode(int val, ListNode next) {
            this.val = val;
            this.next = next;
        }
    }

    public static ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        int sum;
        int carry = 0;
        ListNode out = new ListNode(0);
        ListNode temp = out;
        while (l1 != null || l2 != null || carry != 0) {
            sum = carry;
            if (l1 != null) {
                sum += l1.val;
                l1 = l1.next;
            }
            if (l2 != null) {
                sum += l2.val;
                l2 = l2.next;
            }
            carry = sum > 9 ? 1 : 0;
            sum = sum > 9 ? sum % 10 : sum;
            temp.next = new ListNode(sum);
            temp = temp.next;
        }
        return out.next;
    }

    public static void main(String[] args) {
        ListNode l1 = new ListNode(9, new ListNode(9, new ListNode(9, new ListNode(9, new ListNode(9, new ListNode(9, new ListNode(9)))))));
        ListNode l2 = new ListNode(9, new ListNode(9, new ListNode(9, new ListNode(9))));
        ListNode add = addTwoNumbers(l1, l2);
        while (add != null) {
            System.out.print(add.val + " ");
            add = add.next;
        }
    }
}

```