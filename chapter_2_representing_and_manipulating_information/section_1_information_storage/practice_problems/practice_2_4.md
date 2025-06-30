# Practice 2.4

Without converting the numbers to decimal or binary, try to solve the following arithmetic problems, giving the answers in hexadecimal. Hint: Just modify the methods you use for performing decimal addition and subtraction to use base 16.

[A.](#a) 0x605C + 0x5 = ____

[B.](#b) 0x605C - 0x20 = ____

[C.](#c) 0x605C + 32 = ____

[D.](#d) 0x60FA - 0x605C = ____

---

## A.

0x605C + 0x5:

Following the book, we can use the same methods as base 10, making sure to keep place in mind when adding.
```
          1
0x  6  0  5  C
0x           5  +
-----------------
0x  6  0  6  1
```

Note that we had to carry `1` after computing `C + 5`.

## B.

0x605C - 0x20:

```
0x  6  0  5  C
0x        2  0  -
-----------------
0x  6  0  3  C
```

## C.

0x605C + 32:

Convert `32 (dec)` to `hex`:
```
32 = 2 * 16 + 0 (2) (16^1)
0 = 0 * 16 + 0  (0) (16^0)
------------------
=> 0x20
```

```
0x  6  0  5  C
0x        2  0  +
-----------------
0x  6  0  7  C
```

## D.

0x60FA - 0x605C:

```
          E  A+E
0x  6  0  F  A
0x  6  0  5  C  -
-----------------
0x  0  0  9  E
```

Note that we had to borrow to compute `A - C`.