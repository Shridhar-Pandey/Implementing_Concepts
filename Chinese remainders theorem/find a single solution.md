***Chinese remainders theorem***

The Chinese Remainder Theorem (CRT) is a mathematical theorem that provides a method to solve a system of linear congruences. In other words, given a set of equations with remainders, it provides a way to find a single solution that satisfies all of them.

The theorem states that if we have a set of equations of the form:

          x ≡ a1 (mod m1)
  
          x ≡ a2 (mod m2)
  
          ...
  
          x ≡ ak (mod mk)
  

where m1, m2, ..., mk are pairwise relatively prime positive integers, then there exists a unique solution for x modulo M, where M = m1 * m2 * ... * mk.
  
Furthermore, the solution can be expressed as:

          x = (a1 * M1 * y1 + a2 * M2 * y2 + ... + ak * Mk * yk) mod M

where Mi = M / mi, and yi is the inverse of Mi modulo mi. In other words, yi satisfies:

     Mi * yi ≡ 1 (mod mi)

To use the Chinese Remainder Theorem, we first need to check that the moduli are pairwise relatively prime. Then, we can compute the values of Mi and yi, and use them to compute the solution x.
       
The Chinese Remainder Theorem has many practical applications, including cryptography, computer science, and number theory. It is used, for example, in the RSA cryptosystem, which is widely used to encrypt and decrypt messages in secure communication.
  
  
 <hr>
 ***Pseudocode***
 
``` pseudocode

// Input: A set of equations x ≡ a1 (mod m1), x ≡ a2 (mod m2), ..., x ≡ ak (mod mk)
// Output: The unique solution x modulo M, where M = m1 * m2 * ... * mk

function chinese_remainder_theorem(a, m):
// Compute M = m1 * m2 * ... * mk
M = 1
for i = 1 to k:
M = M * m[i]

// Compute Mi = M / mi for each i
Mi = []
for i = 1 to k:
    Mi[i] = M / m[i]

// Compute the inverse yi of Mi modulo mi for each i
yi = []
for i = 1 to k:
    yi[i] = modular_inverse(Mi[i], m[i])

// Compute x = (a1 * M1 * y1 + a2 * M2 * y2 + ... + ak * Mk * yk) modulo M
x = 0
for i = 1 to k:
    x = x + a[i] * Mi[i] * yi[i]
x = x mod M

return x
```

<hr>

***Python implementation code***

``` py
# Chinese Remainder Theorem algorithm

def chinese_remainder_theorem():
    # Take input from user
    num_eqns = int(input("Enter the number of equations: "))
    a = []
    m = []
    for i in range(num_eqns):
        a_i = int(input(f"Enter a{i+1}: "))
        m_i = int(input(f"Enter m{i+1}: "))
        a.append(a_i)
        m.append(m_i)

    # Compute M = m1 * m2 * ... * mk
    M = 1
    for i in range(len(m)):
        M *= m[i]

    # Compute Mi = M / mi for each i
    Mi = [0] * len(m)
    for i in range(len(m)):
        Mi[i] = M // m[i]

    # Compute the inverse yi of Mi modulo mi for each i
    yi = [0] * len(m)
    for i in range(len(m)):
        yi[i] = pow(Mi[i], -1, m[i])

    # Compute x = (a1 * M1 * y1 + a2 * M2 * y2 + ... + ak * Mk * yk) modulo M
    x = 0
    for i in range(len(m)):
        x += a[i] * Mi[i] * yi[i]
    x %= M

    return x

# Test the function
print("Chinese Remainder Theorem Calculator")
x = chinese_remainder_theorem()
print(f"The unique solution x modulo M is: {x}")
```

<hr>

***Java implementation code***

```java

import java.util.Scanner;

public class ChineseRemainderTheorem {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Take input from user
        System.out.print("Enter the number of equations: ");
        int numEqns = scanner.nextInt();
        int[] a = new int[numEqns];
        int[] m = new int[numEqns];
        for (int i = 0; i < numEqns; i++) {
            System.out.printf("Enter a%d: ", i + 1);
            a[i] = scanner.nextInt();
            System.out.printf("Enter m%d: ", i + 1);
            m[i] = scanner.nextInt();
        }

        // Compute M = m1 * m2 * ... * mk
        int M = 1;
        for (int i = 0; i < m.length; i++) {
            M *= m[i];
        }

        // Compute Mi = M / mi for each i
        int[] Mi = new int[m.length];
        for (int i = 0; i < m.length; i++) {
            Mi[i] = M / m[i];
        }

        // Compute the inverse yi of Mi modulo mi for each i
        int[] yi = new int[m.length];
        for (int i = 0; i < m.length; i++) {
            yi[i] = modInverse(Mi[i], m[i]);
        }

        // Compute x = (a1 * M1 * y1 + a2 * M2 * y2 + ... + ak * Mk * yk) modulo M
        int x = 0;
        for (int i = 0; i < m.length; i++) {
            x += a[i] * Mi[i] * yi[i];
        }
        x %= M;

        System.out.printf("The unique solution x modulo M is: %d", x);

        scanner.close();
    }

    // Computes the modular inverse of a modulo m using the extended Euclidean algorithm
    public static int modInverse(int a, int m) {
        int m0 = m, t, q;
        int x0 = 0, x1 = 1;
        if (m == 1) {
            return 0;
        }
        while (a > 1) {
            // q is quotient
            q = a / m;
            t = m;
            // m is remainder now, process same as Euclid's algorithm
            m = a % m;
            a = t;
            t = x0;
            x0 = x1 - q * x0;
            x1 = t;
        }
        // Make x1 positive
        if (x1 < 0) {
            x1 += m0;
        }
        return x1;
    }
}
```



