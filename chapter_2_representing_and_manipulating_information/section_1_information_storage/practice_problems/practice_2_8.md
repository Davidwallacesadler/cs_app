# Practice 2.8

Fill in the following table showing the results of evaluating Boolean operations on bit vectors.

| row     | Operation | Result     | 
| ------- | --------- | ---------- | 
| _       | `a`       | [01001110] | 
| _       | `b`       | [11100001] | 
| [A](#a) | `~a`      | ___        | 
| [B](#b) | `~b`      | ___        | 
| [C](#c) | `a & b`   | ___        | 
| [D](#d) | `a \| b`  | ___        | 
| [E](#e) | `a ^ b`   | ___        | 

----

## A.

`~a` - "Not a" Just flips all the bits in the vector:
```
01001110
         ~
--------
10110001
```

## B.

`~b`:
```
11100001
         ~
--------
00011110
```

## C.

`a & b` - Bits in each position of either of the vector both need to be 1 for the result to be 1, otherwise 0:
```
01001110
11100001 &
--------
01000000
```

## D.

`a | b` - Bits in each position of either vector just need to be 1 for the result to be 1:
```
01001110
11100001 |
--------
11101111
```

## E.

`a ^ b` - Only one vector can have a 1 in a particular position for the result to be 1:
```
01001110
11100001 ^
--------
10101111
```