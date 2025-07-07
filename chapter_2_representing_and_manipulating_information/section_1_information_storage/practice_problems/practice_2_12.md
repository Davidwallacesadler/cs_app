# Practice 2.12

Write C expressions, in terms of variable `x`, for the following values. Your code should work for any word size `w >= 8`. For reference, we show the result of evaluating expressions for `x = 0x87654321`, with `w = 32`.

A. The least significant byte of x, with all other bits set to 0. `[0x00000021]`

B. All but the least significant byte of x complemented, with the least significant byte left unchanged. `[0x789ABC21]`

C. The least significant byte set to all ones, and all other bytes of x left unchanged `[0x876543FF]`

---

## A.

The least significant byte of x, with all other bits set to 0. `[0x00000021]`

Given that only the least significant byte is all that remains we could apply a `&` operation on a bitmask to acheive this:

```
x & 0xFF

0x87654321
0x      FF &
------------
0x00000021
```

So we have:

```c
int main() {
    unsigned x = 0x87654321
    unsigned res = x & 0xFF

    printf("Result = 0x%x\n", res)
}
```

## B.

All but the least significant byte of x complemented, with the least significant byte left unchanged. `[0x789ABC21]`

Given that we want the complement we can use a similar idea to A. Since `0xFF` has the result of saving the least significant byte we know that must be in our solution somewhere. If we complement x and `0xFF` we zero out the least significant byte and get the complement of x.

```
x & 0xFF (Save the least-significant byte)
~x & ~0xFF (Complement x and zero out the least-significant byte)

=> (x & 0xFF) | (~x & ~0xFF)

0x87654321
0x      FF &
------------
0x00000021

~x = 0x789ABCDE

0x789ABCDE
0xFFFFFF00 &
------------
0x789ABC00

Finally,

0x789ABC00
0x00000021 |
------------
0x789ABC21
```

So we have:

```c
int main() {
    unsigned x = 0x87654321
    unsigned res = (x & 0xFF) | (~x & ~0xFF)
    unsigned res2 = x ^ ~0xFF // Above is defn of xor!

    printf("Result = 0x%x\n", res)
    printf("Result2 = 0x%x\n", res2)
}
```

## C.

The least significant byte set to all ones, and all other bytes of x left unchanged `[0x876543FF]`

We could just use the same bitmask with an or `|` to accomplish this:

```
0x87654321
0x000000FF |
------------
0x876543FF
```

So we have:

```c
int main() {
    unsigned x = 0x87654321
    unsigned res = x | 0xFF

    printf("Result = 0x%x\n", res)
}
```

