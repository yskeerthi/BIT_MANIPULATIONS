
1. **Check if the given number is even or odd**:  
   Use the bitwise AND operator:
   - `n & 1 == 0` → Even
   - `n & 1 == 1` → Odd  
   The least significant bit (LSB) of an odd number is always 1, and for even numbers, it is 0.

2. **Check if the given number is a power of 2**:  
   A number is a power of 2 if it has only one set bit. You can check this with:
   - `n > 0 && (n & (n - 1)) == 0`

3. **Playing with the k-th bit**:
   - To set the k-th bit: `n = n | (1 << k)`
   - To clear the k-th bit: `n = n & ~(1 << k)`
   - To toggle the k-th bit: `n = n ^ (1 << k)`
   - To check the k-th bit: `(n & (1 << k)) != 0`

4. **Multiply or divide a number by 2^k**:  
   - Multiply by `2^k`: Shift left: `n << k`
   - Divide by `2^k`: Shift right: `n >> k`

5. **Find `x % 2^k`**:  
   To get the remainder when dividing by `2^k`, use:
   - `x & ((1 << k) - 1)`  
   This extracts the lowest k bits of `x`.

6. **Swapping two numbers `x` and `y` without using a temporary variable**:  
   Use XOR for swapping:
   - `x = x ^ y`
   - `y = x ^ y`
   - `x = x ^ y`

7. **Property: number of set bits**:  
   To count the number of set bits (Hamming weight) in a number `n`, use:
   - Use Kernighan’s algorithm:  
     ```  
     while (n > 0) {
         n = n & (n - 1);  // clears the lowest set bit
         count++;
     }
     ```

Adding Two Numbers Using Bitwise Operators
To add two numbers using bitwise operators, we need to simulate how addition works at the binary level, which involves handling both the sum and the carry.

Steps:
Sum: XOR (^) the two numbers. This simulates adding the numbers without considering the carry.
Carry: AND (&) the two numbers and left-shift (<<) the result by 1. This simulates the carry part of the addition.
Repeat the process until there is no carry left.
Algorithm:
python
Copy code
def add(a, b):
    while b != 0:
        # Sum without carry
        sum = a ^ b
        
        # Carry
        carry = (a & b) << 1
        
        # Update a and b for the next iteration
        a = sum
        b = carry
    
    return a
