# Practice 2.21

Assuming the expressions are evaluated when executing a 32-bit program on a machine that uses two's complement aritmetic, fill in the following table describing the effects of casting and relational operations, in the style of figure 2.19:

| row     | expression                   | type | evaluation |
| ------- | ---------------------------- | ---- | ---------- | 
| [A.](#a)| -2147483647-1 == 2147483648U | ___  | ___        |
| [B.](#b)| -2147483647-1 < 2147483647   | ___  | ___        |
| [C.](#c)| -2147483647-1U < 2147483647  | ___  | ___        |
| [D.](#d)| -2147483647-1 < -2147483647  | ___  | ___        |
| [E.](#e)| -2147483647-1U < -2147483647 | ___  | ___        |

---

## A.
-2147483647-1 == 2147483648U:

This is an equality comparison operator between a signed and unsigned integer.

The LHS is defined as Tmin32 (Two's complement min for a 32-bit word), and the RHS is defied as Umax32 (Unisgned max for a 32-bit word).

Type:
From figre 2.19 and the fact that this is an equality comparison between a signed and unsigned int we know that C promotes this expression to be `Unsigned`.

Evaluation:
Since the RHS operand is unsigned, the LHS signed operand is casted to an unsigned number:

```
 -2147483647-1 == 2147483648U
= 2147483648U == 2147483648U (after casting)
= 1
```
## B.
-2147483647-1 < 2147483647

This is a relational operator between two signed integers.

The LHS is Tmin32 and the RHS is Tmax32.

Type:
From figure 2.19 and the fact that this is a relational operator between two signed ints we know that C promotes this expression to be `Signed`.

Evaluation:
```
-2147483647-1 < 2147483647
= Tmin32 < Tmax32
= 1
```

## C.
-2147483647-1U < 2147483647

The subtraction of `1U` on the LHS means that `-2147483647` will be casted to an unsigned number so this makes the relational operator be between a unsigned number and a signed number.

Type:
From figure 2.19 and the fact that the LHS will evaluate to unsigned we know that C promotes this expression to be `Unsigned`.

Evaluation:
```
-2147483647-1U < 2147483647
= 2147483647U-1U < 2147483647
= 2147483646U < 2147483647U
= 0
```

## D.
-2147483647-1 < -2147483647

This is a relational operator between two signed integers.

Type:
From figure 2.19 and the fact that both sides are signed we know that C promotes this expression to be `Signed`.

Evaluation:
```
-2147483647-1 < -2147483647
= Tmin32 < -2147483647
= 1
```

## E.
-2147483647-1U < -2147483647

The subtraction of `1U` on the LHS means that `-2147483647` will be casted to an unsigned number so this makes the relational operator be between a unsigned number and a signed number.

Type:
From figure 2.19 and the fact that LHS will evaluate to unsigned we know that C promotes this expression to be `Unsigned`.

Evaluation:
```
-2147483647-1U < -2147483647
= 2147483647U-1U < -2147483647
= 2147483646U < -2147483647
= 2147483646U < 2147483647U
= 1
```