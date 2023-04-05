



















<hr>

***Implementation in PYTHON***

``` py

n = int(input())
bulbs = [True] * n   # Initialize all bulbs to True

def toggle_bulbs(bulbs, multiple):
    for i in range(multiple-1, len(bulbs), multiple):
        bulbs[i] = not bulbs[i]

# Turn off all bulbs
bulbs = [False] * len(bulbs)
print("All bulbs are turned off:", bulbs)

# Toggle bulbs based on multiples
for i in range(1, len(bulbs)+1):
    toggle_bulbs(bulbs, i)
    print("After toggling multiple of", i, ":", bulbs)

# Count number of True values
num_true = bulbs.count(True)
print("Number of bulbs that are on:", num_true)

```
<hr>

***Implementation in JAVA***


``` java 

import java.util.Scanner;
import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        int n = input.nextInt();
        boolean[] bulbs = new boolean[n];

        // Initialize all bulbs to true
        for (int i = 0; i < bulbs.length; i++) {
            bulbs[i] = false;
        }

        // Define the toggleBulbs method
        for (int i = 1; i <= bulbs.length; i++) {
            toggleBulbs(bulbs, i);
            System.out.println("After toggling multiple of " + i + ": " + Arrays.toString(bulbs));
        }

        // Count the number of true values
        int numTrue = 0;
        for (int i = 0; i < bulbs.length; i++) {
            if (bulbs[i]) {
                numTrue++;
            }
        }
        System.out.println("Number of bulbs that are on: " + numTrue);
    }

    public static void toggleBulbs(boolean[] bulbs, int multiple) {
        for (int i = multiple - 1; i < bulbs.length; i += multiple) {
            bulbs[i] = !bulbs[i];
        }
    }
}









