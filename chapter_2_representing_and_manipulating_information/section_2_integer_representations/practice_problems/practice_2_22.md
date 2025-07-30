# Practice 2.22

Show that each of the following bit vectors is a two's-complement representation of -4 by applying Equation 2.3:

Equation 2.3: Def'n of two's-complement encoding.

[A.](#a) [1100]

[B.](#b) [11100]

[C.](#c) [111100]

Observe that the second and third bit vectors can be derived from the first by sign extension.

---

## A.

[1100]

```
 [1100] (two's-complement)
= (-1 * 2^3) + (1 * 2^2) + (0 * 2^1) + (0 * 2^0)
= -8 + 4
= -4
```

## B.

[11100]

```
 [11100] (two's-complement)
= (-1 * 2^4) + (1 * 2^3) + (1 * 2^2) + (0 * 2^1) + (0 * 2^0)
= -16 + 8 + 4
= -4
```

## C.

[111100]

```
 [111100] (two's-complement)
= (-1 * 2^5) + (1 * 2^4) + (1 * 2^3) + (1 * 2^2) + (0 * 2^1)  + (0 * 2^0)
= -32 + 16 + 8 + 4
= -4
```

This shows that sign extension on a two's-complement encoded number keeps the value the same! 