### Task 7 kyu

[Task link](https://www.codewars.com/kata/560a4962c0cc5c2a16000068)

Not considering number 1, the integer 153 is the first integer having this property: the sum of the third-power of each of its digits is equal to 153. Take a look: 153 = 1³ + 5³ + 3³ = 1 + 125 + 27 = 153

The next number that experiments this particular behaviour is 370 with the same power.

Write the function eq_sum_powdig(), that finds the numbers below a given upper limit hMax (inclusive) that fulfills this property but with different exponents as the power for the digits.

eq_sum_powdig(hMax, exp): ----> sequence of numbers (sorted list) (Number one should not be considered).

Let's see some cases:

eq_sum_powdig(100, 2) ----> []

eq_sum_powdig(1000, 2) ----> []

eq_sum_powdig(200, 3) ----> [153]

eq_sum_powdig(370, 3) ----> [153, 370]

### My solution

```Java
import static org.junit.Assert.*;
import org.junit.Test;
import java.util.ArrayList;
import java.util.Arrays;

class Sumpowdig {
    public static void main(String args[]) {

    }

    public static Integer[] eqSumPowDig(long Hmax, long exp)
    {
        ArrayList<Integer> ans = new ArrayList<Integer>();
        for (int i = 2; i <= Hmax; i++)
        {
            int num = i;
            int sum = 0;
            int digit = 0;
            while (num != 0)
            {
                digit = num % 10;
                for (int j = 1; j < exp; j++)
                {
                    digit = digit * (num % 10);
                }
                sum = sum + digit;
                num = num / 10;
            }
            if (sum == i) ans.add(sum);
        }
        Integer[] objects = ans.toArray(new Integer[0]);
        return objects;
    }
}
```

### Favourite solution from code-wars

```Java
import static java.util.stream.LongStream.rangeClosed;

class Sumpowdig {
  static long[] eqSumPowDig(long hmax, int exp) {
    return rangeClosed(2, hmax)
        .filter(n -> (n + "").chars().mapToLong(d -> (long) Math.pow(d - 48, exp)).sum() == n)
        .toArray();
  }
}
```

It's much shorter than my solution and author used interesting tricks!

# Have a nice day!