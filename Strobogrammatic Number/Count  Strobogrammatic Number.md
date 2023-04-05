

***what is Strobogrammatic number***


A number is said to be strobogrammatic if its numeral is rotationally symmetric, or the same when turned 180 degrees. In other terms, the number appears the same both upside down and right-side up (for example, 69, 96, and 1001). Numerous disciplines, including mathematics, computer science, and encryption, use the idea of strobogrammatic numbers.

The numbers 0, 1, and 8 are symmetrical about the horizontal plane when written using standard characters (ASCII), and 6 and 9 are identical when rotated 180 degrees. The initial strobogrammatic numbers in such a scheme are as follows:

0, 1, 8, 11, 69, 88, 96, 101, 111, 181, 609, 619, 689, 808, 818, 888, 906, 916, 986, 1001, 1111, 1691, 1881, 1961, 6009, 6119, 6699, 6889, 6969, 8008, 8118, 8698, 8888, 8968, 9006

Strobogrammatic numbers are used in various applications such as:

*-Cryptography*

*-Number theory*

*-Computer vision*

*-Image processing*

*-Robotics*

For example, strobogrammatic numbers can be used in cryptography to generate safe passwords that are simple to remember but challenging to crack. They can also be used in computer vision and image processing to find strobograms in pictures.


***Algorithm used in Strobogrammatic number***

There are different algorithms that can be used to generate strobogrammatic numbers of a given length. One such algorithm is Depth First Search Algorithm.

The algorithm can be used to bruteforce all possibilities with given size N, then use a routine to check if it is a valid strobogrammatic number. Another algorithm that can be used to check if an integer is a strobogrammatic number is Recursive Depth First Search Algorithm


steps to generate strobogrammatic numbers using Depth First Search Algorithm in more detail:

1.Create a list of strobogrammatic numbers of length 0 and 1.

2.For each iteration, add a pair of strobogrammatic numbers of length n+2 by adding a pair of strobogrammatic numbers of length n to both sides of each strobogrammatic number of length n-2.

3.If n is odd, add “0”, “1”, “8” to the middle of each strobogrammatic number of length n-1.

For example, let’s say we want to generate all strobogrammatic numbers with length 4. We start with a list containing [“11”, “69”, “88”, “96”, “00”]. Then we add a pair of strobogrammatic numbers of length 4 by adding a pair of strobogrammatic numbers of length 2 to both sides of each strobogrammatic number of length 0. We get [“1111”, “6969”, “8888”, “9696”, “0000”]. Then we add a pair of strobogrammatic numbers of length 4 by adding a pair of strobogrammatic numbers of length 2 to both sides of each strobogrammatic number of length 2. We get [“1111”, “6969”, “8888”, “9696”, “0000”, “11611”, “9669”, “98689”, “69696”, “10001”]. Finally, we add “0”, “1”, “8” to the middle of each strobogrammatic number of length 3 (which is odd). We get [“1111”, “6969”, “8888”, “9696”, “0000”, “11611”, “9669”, “98689”, “69696”, “10001”,“10101”,“18181”,“11111”,“16991”,“18881”,“19661”,“19861”.



















<hr>

***Implementation in Python***

```py
def strobogrammatic_no(n):
    result = num(n, n)
    return result

def num(n, length):
    if n == 0:
        return [""]
    if n == 1:
        return ["0", "1", "8"]
    if n == 2:
        return ["11", "69", "88", "96"]
    middle = num(n - 2, length)
    result = []
    for m in middle:
        if n != length:
            result.append("0" + m + "0")
        result.append("1" + m + "1")
        result.append("6" + m + "9")
        result.append("8" + m + "8")
        result.append("9" + m + "6")
    return result

n = int(input())
print(strobogrammatic_no(n))

```


<hr>


***Implementation in java***

``` java
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class StrobogrammaticNumber {
    public static List<String> strobogrammaticNo(int n) {
        return num(n, n);
    }

    public static List<String> num(int n, int length) {
        if (n == 0) {
            List<String> result = new ArrayList<>();
            result.add("");
            return result;
        }
        if (n == 1) {
            List<String> result = new ArrayList<>();
            result.add("0");
            result.add("1");
            result.add("8");
            return result;
        }
        if (n == 2) {
            List<String> result = new ArrayList<>();
            result.add("11");
            result.add("69");
            result.add("88");
            result.add("96");
            return result;
        }
        List<String> middle = num(n - 2, length);
        List<String> result = new ArrayList<>();
        for (String m : middle) {
            if (n != length) {
                result.add("0" + m + "0");
            }
            result.add("1" + m + "1");
            result.add("6" + m + "9");
            result.add("8" + m + "8");
            result.add("9" + m + "6");
        }
        return result;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter the value of n: ");
        int n = scanner.nextInt();
        List<String> result = strobogrammaticNo(n);
        System.out.println(result);
    }
}
