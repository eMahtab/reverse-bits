# Reverse Bits
## https://leetcode.com/problems/reverse-bits

Reverse bits of a given 32 bits unsigned integer.
```
Example 1:

Input: 00000010100101000001111010011100
Output: 00111001011110000010100101000000
Explanation: The input binary string 00000010100101000001111010011100 represents the unsigned integer 43261596, so return 964176192 which its binary representation is 00111001011110000010100101000000.

Example 2:

Input: 11111111111111111111111111111101
Output: 10111111111111111111111111111111
Explanation: The input binary string 11111111111111111111111111111101 represents the unsigned integer 4294967293, so return 3221225471 which its binary representation is 10111111111111111111111111111111.
``` 

**Note:**

1. Note that in some languages such as Java, there is no unsigned integer type. In this case, both input and output will be given as signed integer type and should not affect your implementation, as the internal binary representation of the integer is the same whether it is signed or unsigned.

2. In Java, the compiler represents the signed integers using 2's complement notation. Therefore, in Example 2 above the input represents the signed integer -3 and the output represents the signed integer -1073741825.
 
**Follow up:**

If this function is called many times, how would you optimize it?

## Approach :
Quick recap about `AND` operator
```
1 & 1 = 1
0 & 1 = 0
```
So we will do `AND` operation (& 1) to retrieve the bit

Quick recap about `OR` operator
```
0 | 0 = 0
1 | 0 = 1
```
So we will do `OR` operation (| bit) to insert the bit into result.

Iterate over the 32 bit unsigned number and do the following operations :

1. First do the `& 1` operation with input n, this will give us the bit
2. Right shift the input n by 1 (n >> 1), for the next iteration
3. Next Left shift the result by 1 (result << 1) to make the space, so now the last bit of result will be 0
4. Do the `OR` operation with the bit in Step 1 (result | bit)


## Implementation :
```java
public class Solution {
    // you need treat n as an unsigned value
    public int reverseBits(int n) {
        int result = 0;
        for (int i = 0; i < 32; i++) {
            int bit = n & 1;
            n = n >> 1;
            result = result << 1;
            result = result | bit;
        }
        return result;
    }
}
```

# References :
1. https://www.youtube.com/watch?v=KE5Axm7uzok
2, https://developersinspired.com/2020/03/02/how-to-reverse-bits-bit-manipulation


