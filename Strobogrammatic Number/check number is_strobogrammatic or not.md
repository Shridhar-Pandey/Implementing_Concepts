
***Python Implementation code***


```py
def is_strobogrammatic(n):
    strobogrammatic = {'0': '0', '1': '1', '6': '9', '8': '8', '9': '6'}
    s = str(n)
    for i in range((len(s) + 1) // 2):
        if s[i] not in strobogrammatic or s[-i - 1] != strobogrammatic[s[i]]:
            return False
    return True

number = input("Enter a number to check if it's a Strobogrammatic Number: ")
if is_strobogrammatic(number):
    print(f"{number} is a Strobogrammatic Number!")
else:
    print(f"{number} is not a Strobogrammatic Number.")
```
                   
<hr>


***Java Implementation code***

``` java
import java.util.*;

public class StrobogrammaticNumber {
    public static boolean isStrobogrammatic(String n) {
        Map<Character, Character> strobogrammatic = new HashMap<>();
        strobogrammatic.put('0', '0');
        strobogrammatic.put('1', '1');
        strobogrammatic.put('6', '9');
        strobogrammatic.put('8', '8');
        strobogrammatic.put('9', '6');

        for (int i = 0; i < (n.length() + 1) / 2; i++) {
            char c = n.charAt(i);
            if (!strobogrammatic.containsKey(c) || n.charAt(n.length() - i - 1) != strobogrammatic.get(c)) {
                return false;
            }
        }
        return true;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter a number to check if it's a Strobogrammatic Number: ");
        String number = sc.next();

        if (isStrobogrammatic(number)) {
            System.out.println(number + " is a Strobogrammatic Number!");
        } else {
            System.out.println(number + " is not a Strobogrammatic Number.");
        }
    }
}
```
