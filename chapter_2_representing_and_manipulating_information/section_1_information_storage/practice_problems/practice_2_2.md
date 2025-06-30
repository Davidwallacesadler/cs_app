# Practice 2.2

Fill in the blank entires in the following table, giving the decimal and hexadecimal representation of different powers of 2:

| row     | n       | 2^n dec | 2^n hex |
| ------- | ------- | ------- | ------- |
| [A.](#a)| 5       | 32      | 0x20    |
| [B.](#b)| 23      | _       | _       |
| [C.](#c)| _       | 32,768  | _       |
| [D.](#d)| _       | _       | 0x2000  |
| [E.](#e)| 12      | _       | _       |
| [F.](#f)| _       | 64      | _       |
| [G.](#g)| _       | _       | 0x100   |

---

## A.

Given `n = 5`:

`Decimal` - We can calculate the decimal representation using successive multiplication:
```
2^5 
=> (2 * 2) * 2 * 2 * 2
=> (4 * 2) * 2 * 2
=> (8 * 2) * 2
=> 16 * 2
----------------------
=> 32
```

`Hex` - We can think about the the binary representation then can easily translate that into hex:

2^5 => 6 digit binary number (Noting that the first digit starts at 2^0):
```
_   _   _   _   _   _     
|   |   |   |   |   |  =>  1   0   0   0   0   0
32  16  8   4   2   1     
```

Now we convert `100000 (bin)` to `hex`:
```
   100000
   0010 0000
0x    2    0
------------
=> 10000 == 0x20
```

## B.

Given `n = 23`:

`Decimal`:
```
2^23 
=> (2 * 2) * 2 * 2 * 2 ... * 2 // Just use a damn calculator...
-------------
=> 8,388,608
```

`Hex`:
2^23 => 24 digit binary number
```
   100000000000000000000000
   1000 0000 0000 0000 0000 0000
0x    8    0    0    0    0    0
--------------------------------
=> 0x800000
```

## C.

Given `2^n = 32,768`:

`n` - We can get n using `log2` and solving for `n`:
```
2^n = 32,768
=> log2(2^n) = log2(32,768)
=> log2(2) * n = log2(32,768)
=> 1 * n = log2(32,768)
----------------------------
=> n = 15 
```

`Hex`:
2 ^ 15 => 16 digit binary number
```
   1000000000000000
   1000 0000 0000 0000
0x    8    0    0    0 
----------------------
=> 0x8000
```

## D.

Given `0x2000`:

`n`:
```
0x    2    0    0    0 
   0010 0000 0000 0000
----------------------
=> n = 13
```

`Decimal`:
```
2^13 
=> (2 * 2) * 2 * 2 * 2 ... * 2 // Just use a damn calculator...
-------------
=> 8,192
```

## E.

Given `n = 12`:

`Decimal`:
```
2^12
=> (2 * 2) * 2 * 2 * 2 ... * 2 // Just use a damn calculator...
-------------
=> 4,096
```

`Hex`:
2 ^ 12 => 13 digit binary number
```
   1000000000000
   0001 0000 0000 0000
0x    1    0    0    0 
----------------------
=> 0x1000
```

## F.

Given `2^n = 64`:

`n` - We can get n using `log2` and solving for `n`:
```
2^n = 64
=> log2(2^n) = log2(64)
=> log2(2) * n = log2(64)
=> 1 * n = log2(64)
------------------------
=> n = 6 
```

`Hex`:
2 ^ 6 => 7 digit binary number
```
   1000000
   0100 0000
0x    4    0 
------------
=> 0x40
```

## G.

Given `0x100`:

`n`:
```
0x    1    0    0 
   0001 0000 0000
-----------------
=> n = 8
```

`Decimal`:
```
2^8 
=> (2 * 2) * 2 * 2 * 2 ... * 2 // Just use a damn calculator...
-------------
=> 64
```