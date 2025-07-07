# Practice 2.10

As an application of the property that `a ^ a = 0` for any bit vector `a`, consider the following program:

```c
void inplace_swap(int *x, int *y) {
    *y = *x ^ *y; /* Step 1 */
    *x = *x ^ *y; /* Step 2 */
    *y = *x ^ *y; /* Step 3 */
}
```

As the name implies, we claim that the effect of this procedure is to swap the values stored at the locations denoted by pointer variables x and y. Note that unlike the usual technique of swapping two values, we do not need a third location to temporarily store one value while we are moving the other. There is no performance advantage to this way of swapping; it is mearly an intellectual amausement.

Starting with values `a` and `b` in the locations pointed to by `x` and `y`, respectively, fill in the table that follows, giving the values stored at the two locations after each step of the proceedure. Use the properties of `^` to show that the desired effect is acheived. Recall that every element is its own additive inverse (that is, `a ^ a = 0`).

| step     | *x  | *y  |
| -------- | --- | --- |
| Initial  | a   | b   |
| Step 1   | _   | _   |
| Step 2   | _   | _   |
| Step 3   | _   | _   |

---

Step 1:

```
*y = *x ^ *y
   = a ^ b
------------
=> *x = a, *y = a ^ b
```

Step 2:

```
*x = *x ^ *y
   = a ^ (a ^ b)
   = (a ^ a) ^ b
   = b
------------
=> *x = b, *y = a ^ b
```

Step 2:

```
*y = *x ^ *y
   = b ^ (a ^ b)
   = a ^ (b ^ b)
   = a
------------
=> *x = b, *y = a
```