# Bit Wise Operators
1) Find Unique in a given array
```
  public class FindUnique {
    public static void main(String[] args) {
        int[] arr = {2, 3, 3, 4, 2, 6, 4};
        System.out.println(ans(arr));
    }

    private static int ans(int[] arr) {
        int unique = 0;

        for(int n : arr) {
            unique ^= n;
        }

        return unique;
    }
 }
 Hint : a XOR a = 0
 ```
2) Odd or Even
```
   public class OddEven {

    public static void main(String[] args) {
	    int n = 68;
        System.out.println(isOdd(n));
    }

    private static boolean isOdd(int n) {
        return (n & 1) == 1;
    }
  }
 Hint: IF last bit of a number is 1 then its odd else even. Wecan get last bit number by doing &1 with number
        a &1 = a
```

 3) Power of 2 or not
 
 ```
    public class PowOfTwo {
    public static void main(String[] args) {
        int n = 31; // note: fix for n = 0
        boolean ans = (n & (n-1)) == 0;
        System.out.println(ans);
      }
    }
  Hint: if a is poer of 2 then a & a-1 will be 0
```
 4) Range of XOR
  ```
    public class RangeXOR {
    public static void main(String[] args) {
        // range xor for a, b = xor(b) ^ xor(a-1)
        int a = 3;
        int b = 9;

        int ans = xor(b) ^ xor(a-1);

        System.out.println(ans);

        // only for check, will give TLE for large numbers
        int ans2 = 0;
        for (int i = a; i <= b; i++) {
            ans2 ^= i;
        }

        System.out.println(ans2);
    }

    // this gives xor from 0 to a
    static int xor(int a) {
        if (a % 4 == 0) {
            return a;
        }

        if (a % 4 == 1) {
            return 1;
        }

        if (a % 4 == 2) {
            return a + 1;
        }

        return 0;
    }

  }
 ```
5) Find number of set bits
```
    public class SetBits {
    public static void main(String[] args) {
        int n = 234567;
        System.out.println(Integer.toBinaryString(n));

        System.out.println(setBits(n));
    }

    private static int setBits(int n) {
        int count = 0;

  //        while (n > 0) {
  //            count++;
  //            n -= (n & -n);
  //        }

          while (n > 0) {
              count++;
              n = n & (n-1);
          }

          return count;
      }
  }
 ```   
 6) find nth set bit position number for a
 
    a & (1 << n-1)
 7) reset nth bit position for a
 
    a & !( 1 << n-1)
 8) set nth bit position
 
    a | ( 1<< n-1)
    
 9) Number of digits in base
 
 ```  
     public class NoOfDigits {
      public static void main(String[] args) {
          int n = 10;
          int b = 2;

          int ans = (int)(Math.log(n) / Math.log(b)) + 1;

          System.out.println(ans);
      }
    }
  ```  
    
  10) Fnd the Magic Number
  
  ```  
    public class MagicNumber {
    public static void main(String[] args) {
          int n = 5;

          int ans = 0;
          int base = 5;

          while (n > 0) {
              int last = n & 1;
              n = n >> 1;
              ans += last * base;
              base = base * 5;
          }

          System.out.println(ans);
      }
    }
   ```
      
  11) Prime or not
    
   ```
    public class Prime {
      public static void main(String[] args) {
          int n = 20;
          for (int i = 2; i <= n; i++) {
              System.out.println(i + " " + isPrime(i));
          }
      }

      static boolean isPrime(int n) {
            if (n <= 1) {
                return false;
            }

            int c = 2;
            while (c * c <= n) {
                if (n % c == 0) {
                    return false;
                }
                c++;
            }
            return true;
        }
    }
    
    Sieve of Eratosthenes solution
    
      public class Seive {
    public static void main(String[] args) {
        int n = 40;
        boolean[] primes = new boolean[n+1];
        sieve(n, primes);
    }

    // false in array means number is prime
    static void sieve(int n, boolean[] primes) {
        for (int i = 2; i*i <= n; i++) {
            if (!primes[i]) {
                for (int j = i*2; j <= n; j+=i) {
                    primes[j] = true;
                }
            }
        }

        for (int i = 2; i <= n; i++) {
            if (!primes[i]) {
                System.out.print(i + " ");
            }
        }
       }
    }
    
```
12) Square root of a number
 
 ```
    public class NewtonSQRT {
      public static void main(String[] args) {
          System.out.println(sqrt(40));
      }
      static double sqrt(double n) {
          double x = n;
          double root;
          while (true) {
              root = 0.5 * (x + (n/x)); // is fromula to caluate root of n

              if (Math.abs(root - x) < 0.5) {
                  break;
              }

              x = root;
          }
          return root;
      }
    }

  Binary Search program to find square root of a number
  
    public class BinarySearchSQRT {
        public static void main(String[] args) {
            int n = 40;
            int p = 3;

            System.out.printf("%.3f", sqrt(n, p));
        }

        // Time: O(log(n))
        static double sqrt(int n, int p) {
            int s = 0;
            int e = n;

            double root = 0.0;

            while (s <= e) {
                int m = s + (e - s) / 2;

                if (m * m == n) {
                    return m;
                }

                if (m * m > n) {
                    e = m - 1;
                } else {
                    s = m + 1;
                    root = m;
                }
            }
            double incr = 0.1;
            for (int i = 0; i < p; i++) {
                while (root * root <= n) {
                    root += incr;
                }
                root -= incr;
                incr /= 10;
            }

            return root;
        }
    }
 ```
     
13) Factors of a number
  
 ```
    public class Factors {
        public static void main(String[] args) {
            factors3(20);
        }

        // O(n)
        static void factors1(int n) {
            for (int i = 1; i <= n; i++) {
                if (n % i == 0) {
                    System.out.print(i + " ");
                }
            }
        }

        // O(sqrt(n))
        static void factors2(int n) {
            for (int i = 1; i <= Math.sqrt(n); i++) {
                if (n % i == 0) {
                    if (n/i == i) {
                        System.out.print(i + " ");
                    }else {
                        System.out.print(i + " " + n/i + " ");
                    }
                }
            }
        }

        // both time and space with be O(sqrt(n))
        static void factors3(int n) {
            ArrayList<Integer> list = new ArrayList<>();
            for (int i = 1; i <= Math.sqrt(n); i++) {
                if (n % i == 0) {
                    if (n/i == i) {
                        System.out.print(i + " ");
                    }else {
                        System.out.print(i + " ");
                        list.add(n/i);
                    }
                }
            }
            for (int i = list.size() - 1; i >= 0; i--) {
                System.out.print(list.get(i) + " ");
            }
        }

    }
```
      
14) GCD and LCM of number

 ```
  
    public class GCD_LCM {
    public static void main(String[] args) {
//        System.out.println(gcd(4, 9));
        System.out.println(lcm(2, 7));
    }

    static int gcd(int a, int b) {
        if (a == 0) {
            return b;
        }
        return gcd(b%a, a);
    }

    static int lcm(int a, int b) {
        return a * b / gcd(a, b);
    }
  }
```
  
