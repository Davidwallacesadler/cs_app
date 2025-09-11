# Practice 2.6

Using `show_int` and `show_float`, we determine that the integer `2607352` has hexadecimal value `0x0027C8F8`, while floating-point number `3510593.0` has hexadecimal representation `0x4A1F23E0`

A. Write the binary representations of these two values.
B. Shift these two strings relative to one another to maximize the number of matching bits. How many bits match?
C. What parts of the string do not match?

---

## A.
Write the binary representations of these two values.

`0x0027C8F8`:
```
0x    0    0    2    7    C    8    F    8
   0000 0000 0010 0111 1100 1000 1111 1000
------------------------------------------
=> 0000 0000 0010 0111 1100 1000 1111 1000
```

`0x4A1F23E0`:
```
0x    4    A    1    F    2    3    E    0
   0100 1010 0001 1111 0010 0011 1110 0000
------------------------------------------
=> 0100 1010 0001 1111 0010 0011 1110 0000
```

## B.
Shift these two strings relative to one another to maximize the number of matching bits. How many bits match?

No shift:
```
A: 0001 0000 0010 0111 1100 1000 1111 1000
B: 0100 1010 0001 1111 0010 0011 1110 0000
```

B >> 1 - Just add a `0` to the LHS of B and scoot everything else over.
```
A: 0000 0000 0010 0111 1100 1000 1111 1000
B: 0010 0101 0000 1111 1001 0001 1111 0000
```

B >> 2 - Same as last case:
```
A: 0000 0000 0010 0111 1100 1000 1111 1000
B: 0001 0010 1000 0111 1100 1000 1111 1000
```

We end up with:
```
0000 0000 0010 0111 1100 1000 1111 1000
|||  || |  | | |||| |||| |||| |||| ||||
0001 0010 1000 0111 1100 1000 1111 1000
---------------------------------------
=> 28 matching bits
```

## C.
What parts of the string do not match?

Some of the higher order bits do not match, but many of the lower order ones do. 