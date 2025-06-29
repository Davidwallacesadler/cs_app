# Practice 2.1

Perform the following number conversions:
- A. 0x25B9D2 to binary
- B. binary 1010111001001001 to hexadecimal
- C. 0xA8B3D to binary
- D. binary 1100100010110110010110 to hexadecimal

---

A. We know that each hex digit represents 4-bits so we can solve this by breaking apart the hex value into its hex digits and evaluating each one separately and then bring them together to form the binary representation.

```
0x    2    5    B    9    D    2
   0010 0101 1011 1001 1101 0010

=> 0x25B9D2 == 0010 0101 1011 1001 1101 0010
```
---

B. We can do the inverse operation of A. and group bits of 4 starting at the right (as noted in the book: "if the total number of bits is not a multiple of 4, make the leftmost group be the one with fewer than 4 bits")

```
   1010111001001001
   1010 1110 0100 1001
0x    A    E    4    9

=> 1010 1110 0110 1001 == 0xAE49 
```
---

C. We do the same as A.

```
0x    A    8    B    3    D
   1010 1000 1011 0011 1101

=> 0xA8B3D == 1010 1000 1011 0011 1101
```
---

D. We do the same as B. (making sure to group bits starting at the right and pad with 0s where we have a group of less than 4 bits)

```
   1100100010110110010110
   0011 0010 0010 1101 1001 0110
0x    3    2    2    D    9    6

=> 0011 0010 0010 1101 1001 0110 == 0x322D96
```

