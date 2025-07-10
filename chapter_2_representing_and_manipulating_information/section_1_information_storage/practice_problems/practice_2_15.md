# Practice 2.15

Using only bit-level and logical operations, write a C expression that is equivalent to `x == y`. In other words, it will return 1 when `x` and `y` are equal and 0 otherwise.

---

Using the fact that `x ^ x = 0` for any bit vector `x`, we can assume that if `x ^ y = 0` then we know `x == y`.

If `x` and `y` are equal and `x ^ y = 0` then all we need to do now is apply the logical not operator to invert this expression to return 1 instead of 0: `!(x ^ y)`

For example, given x = `0x75` and y = `0x75` we have:

```
0x75 = 0111 0101

0111 0101
0111 0101 ^
-----------
0000 0000 = 0x00

=> !(0x00) = 0x01 = 1 (as desired)
```

Also, given x = `0x75` and y = `0x36` we have:

```
0x75 = 0111 0101
0x36 = 0011 0110

0111 0101
0011 0110 ^
-----------
0100 0011 = 0x43

=> !(0x43) = 0x00 = 0 (as desired)
```

So we have the following C function that utilizes this expression to check for equality between to unsigned integers:

```c
int isEqual(unsigned x, unsigned y) {
    return !(x ^ y)
}
```