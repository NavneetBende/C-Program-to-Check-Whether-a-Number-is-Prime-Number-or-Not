# C-Program-to-Check-Whether-a-Number-is-Prime-Number-or-Not

Prime Number Program in C
Let’s look at Prime Number Program in C. A number is considered a prime number when it satisfies the below conditions. 

A prime number is a number which can be divided by 1 and itself
A number which can not be divided by any other number other than 1 or itself is a prime number.
It should have only 2 factors. They are, 1 and the number itself.
prime or not in c
Check Whether a Number is Prime Number or Not in C
Given an integer input, the objective is to check whether or not the input integer is a prime or not. In order to do so we check if the number is divisible by 2, if so it’s not a prime. We also divide the numbers with the input until square root of the input, if any of them divides the number perfectly, it’s not a prime.  Here are some of the methods to Check Whether a Number is Prime or Not in C

Method 1: Simple iterative solution
Method 2: Optimization by break condition
Method 3: Optimization by n/2 iterations
Method 4: Optimization by √n
Method 5: Optimization by skipping even iteration
Method 6: Basic Recursion technique
We’ll discuss the above mentioned methods in detail in the upcoming sections.

While loop in C
Method 1: Simple iterative solution
This method uses the assumption that a prime number will exactly have 2 divisors 1 and itself.

Working
For an input num

Initialize count = 0
Run an iterative for loop in iteration of (i) b/w 1 -> num
Check if num is divisible i
If divisible increment count
If num == 0 or num == 1 : Not Prime
If count > 2 : Not prime
Else, it is Prime
Code
Run
#include <stdio.h>  

int main()
{
    int i, count = 0;
    int num = 19;
    
    // checking number of divisors b/w 1 & num
    for(i = 1; i <= num; i++) { if(num % i == 0) count += 1; } // 0 & 1 are not prime number if(num == 0 || num == 1) printf("%d is not prime", num); //if number of divisors are > 2 then not prime else prime 
    else if(count > 2) 
        printf("%d is not prime", num);
    else
    printf("%d is prime", num);

return 0;
}
// Time complexity O(N)
// Space complexity O(1)
Code
19 is Prime
Related Pages
Greatest of the Three numbers

Leap year or not

Prime number within a given range

Sum of digits of a number

Reverse of a number

Method 2: Optimization by break condition
This method uses the assumption that –

All numbers are divisible by 1 and itself
So it is better to check for divisors between [2,n-1]
If any divisor is found, then break the loop and don’t check further as it’s not prime
0, 1 and all negative numbers are not prime
Working
For an input num

Initialize a flat called as isPrime = 1 i.e. true
If num < 2
isPrime = 0
Run an iterative for loop in iteration of (i) b/w 2 -> num -1
Check if num is divisible i
If divisible isPrime = 0 and break loop
If isPrime  == 1 : Prime
Else, it is Not Prime
Code
Run
#include <stdio.h>

int main()
{
    int i,num = 21;
    int isPrime= 1;
    
    
    // 0, 1 and negative numbers are not prime
    if(num < 2){
        isPrime = 0;
    }
    else{   
        // shouldn't have any divisors in b/w 2 & num-1 
        for(i=2; i < num; i++)
        {
            if(num % i == 0)
            {
                isPrime = 0;
                break;
            }
        }
    }

    if(isPrime)
        printf("%d is Prime", num);
    else
        printf("%d is not Prime", num);
 
    return 0;
}
//Time Complexity: O(N)
//Space Complexity O(1)

// This code is better than previous code as we
// 1. Break the loop as soon as we find first divisor
// 2. Loop runs b/w [2,n-1] rather than previous [1, n]
// 3. Condition for 0, 1, neg. nos checked earlier in the code
Output
21 is not prime
Method 3: Optimization by n/2 iterations
This method uses the assumption that –

Checking for divisors b/w [2, n-1] is wasteful
As no number will have any divisor beyond num/2+1
Example: 36 won’t have any divisors between [17, 35]
Working
For an input num

Initialize a flat called as isPrime = 1 i.e. true
If num < 2
isPrime = 0
Run an iterative for loop in iteration of (i) b/w 2 -> num/2
Check if num is divisible i
If divisible isPrime = 0 and break loop
If isPrime  == 1 : Prime
Else, it is Not Prime
Code
Run
 include <stdio.h>

int main()
{
    int i,num = 11;
    int isPrime= 1;
    
    
    // 0, 1 and negative numbers are not prime
    if(num < 2){
        isPrime = 0;
    }
    else{   
    // no need to run loop till num-1 as for any number x the numbers in
    // the range(num/2 + 1, num) won't be divisible anyways.
        int x = num/2;
        for(i=2; i<x; i++)
        {
            if(num % i == 0)
            {
                isPrime = 0;
                break;
            }
        }
    }

    if(isPrime)
        printf("%d is Prime", num);
    else
        printf("%d is not Prime", num);
 
    return 0;
}
//Time Complexity: O(N)
//Space Complexity O(1)

// This code is better than previous code as we
// 1. Loop runs b/w [2,num/2] rather than previous [2, n-1]
// Even though time complexity is same as previous code
// But, this works 2x faster than method 2
Output
11 is Prime
Method 4: Optimization by √n
This method uses the assumption that –

We can simply check all divisors between [2, √num]
Explanation given in code itself
Working
For an input num

Initialize a flat called as isPrime = 1 i.e. true
If num < 2
isPrime = 0
Run an iterative for loop in iteration of (i) b/w 2 -> √num
Check if num is divisible i
If divisible isPrime = 0 and break loop
If isPrime  == 1 : Prime
Else, it is Not Prime
Code
Run
#include <stdio.h> 
#include <math.h>

int main()
{
    int i,num = 17;
    int isPrime= 1;
    
    
    // 0, 1 and negative numbers are not prime
    if(num < 2){
        isPrime = 0;
    }
    else{
    // Number n is not a prime, it can be factored into two factors a & b:
    // n = a * b (Excluding 1 & n)

    /*Now a & b can't be both greater than the square root of n, since
    then the product a * b would be greater than sqrt(n) * sqrt(n) = n.
    So in any factorization of n, at least one of the factors must be
    smaller than the square root of n, and if we can't find any factors
    less than or equal to the square root, n must be a prime.
    */
        for(i=2; i <= sqrt(num); i++)
        {
            if(num % i == 0)
            {
                isPrime = 0;
                break;
            }
        }
    }

    if(isPrime)
        printf("%d is Prime", num);
    else
        printf("%d is not Prime", num);
 
    return 0;
}
//Time Complexity: O(√N)
//Space Complexity O(1)

// This code is better than previous code as we
// 1. Loop runs b/w [2,√num] rather than previous [2, n/2]
Output
17 is Prime
Method 5: Optimization by skipping even iteration
This method uses the assumption that –

We can simply check all divisors between [2, √num]
2 is the only even prime number
We can skip all even iterations in the loop
Code
#include <stdio.h>
#include <math.h>

int isPrime(int n){
    // 0 and 1 are not prime numbers
    // negative numbers are not prime
    if (n <= 1)
        return 0;

    // special case as 2 is the only even number that is prime
    else if (n == 2)
        return 1;

    // Check if n is a multiple of 2 thus all these won't be prime
    else if (n % 2 == 0)
        return 0;

    // If not, then just check the odds
    for (int i = 3; i <= sqrt(n); i += 2)
    {
        if (n % i == 0)
            return 0;
    }
    
    return 1;
}

int main() {
    int num=23;
    
    if (isPrime(num))
        printf("%d is prime", num);
    else
        printf("%d is not prime", num);

    return 0;
}
//Time complexity : O(√N)
//Space complexity : O(1)

//This code is better than previous code
// 1. We skipping all even iterations b/w [3, √num]
// Works almost 2x faster than method 4
Output
23 is Prime
Method 6: Basic Recursion technique
This method uses recursion, the code below is self-explanatory-

Initialize i =2, Start with checkPrime(num, i)
In each recursion call check if ‘i’ is a divisor of num
If i is divisor return 0: means not prime
else increment the value of i to check for the next possible divisor in the next recursion
Keep doing this until recursion from 2 to n
Code
#include <stdio.h>

int checkPrime(int n, int i)
{
    // we check if i is divisor of n or not here
    
    // 0, 1 & neg. nos are not prime
    if (n < 2)
        return 0;
    
    // if this satisfies then its prime as we
    // have completed recursion from 2 to n
    if (i == n)
        return 1;

    // Base cases
    if (n % i == 0)
        return 0;
       
    // none of above condition matches
    // keep checking for next divisor in i+1 recursion call
    i += 1;
    
    return checkPrime(n, i);
}
int main()
{
    int i=2;
    int num = 19;
    
    if(checkPrime(num, i))
        printf("%d is Prime",num);
    else
        printf("%d is Not Prime",num);

    return 0;
}
// Time complexity: O(N)
// Space complexity: O(1)
// Auxilary Space complexity: O(N)
// Due to function call stack
Output
19 is Prime
