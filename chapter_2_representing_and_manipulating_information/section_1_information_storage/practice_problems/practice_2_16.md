# Practice 2.16

Fill in the table below showing the effects of the different shift operations on single byte quantities. The best way to think about shift operations is to work with binary representations. Convert the initial values to binary, perform the shifts, and then convert back to hexadecimal. Each of the answers should be 8 binary digits or 2 hexadecimal digits. Note: `L` below stands for Logical Shift, and `A` stands for Arithmetic Shift.

| row     | a              | a << 2    | a >> 3 (L) | a >> 3 (A) |
| ------- | ---------------| --------- | ---------- | ---------- |
| [A](#a) | Hex: 0xD4, Bin:| Bin:, Hex:| Bin:, Hex: | Bin:, Hex: |
| [B](#b) | Hex: 0x64, Bin:| Bin:, Hex:| Bin:, Hex: | Bin:, Hex: |
| [C](#c) | Hex: 0x72, Bin:| Bin:, Hex:| Bin:, Hex: | Bin:, Hex: |
| [D](#d) | Hex: 0x44, Bin:| Bin:, Hex:| Bin:, Hex: | Bin:, Hex: |

---

## A.

`0xD4` to bin:
```
0x   D    4
  1101 0100
-----------
=> 0xd4 = 1101 0100
```

`0xD4 << 2`:
```
1101 0100 << 2
--------------
0101 0000 (bin)
0x50 (hex)
```

`0xD4 >> 3 (L)`:
```
1101 0100 >> 3 (L)
------------------
0001 1010 (bin)
0x1A (hex)
```

`0xD4 >> 3 (A)`:
```
1101 0100 >> 3 (A)
------------------
1111 1010 (bin)
0xFA (hex)
```

## B.

`0x64` to bin:
```
0x   6    4
  0110 0100
-----------
=> 0x64 = 0110 0100
```

`0x64 << 2`:
```
0110 0100 << 2
--------------
1001 0000 (bin)
0x90 (hex)
```

`0x64 >> 3 (L)`:
```
0110 0100 >> 3 (L)
------------------
0000 1100 (bin)
0x0C (hex)
```

`0x64 >> 3 (A)`:
```
0110 0100 >> 3 (A)
------------------
0000 1100 (bin)
0x0C (hex)
```

## C.

`0x72` to bin:
```
0x   7    2
  0111 0010
-----------
=> 0x72 = 0111 0010
```

`0x72 << 2`:
```
0111 0010 << 2
--------------
1100 1000 (bin)
0xC8 (hex)
```

`0x72 >> 3 (L)`:
```
0111 0010 >> 3 (L)
------------------
0000 1110 (bin)
0x0E (hex)
```

`0x72 >> 3 (A)`:
```
0111 0010 >> 3 (A)
------------------
0000 1110 (bin)
0x0E (hex)
```

## D.

`0x44` to bin:
```
0x   4    4
  0100 0100
-----------
=> 0x44 = 0100 0100
```

`0x44 << 2`:
```
0100 0100 << 2
--------------
0001 0000 (bin)
0x10 (hex)
```

`0x44 >> 3 (L)`:
```
0100 0100 >> 3 (L)
------------------
0000 1000 (bin)
0x08 (hex)
```

`0x44 >> 3 (A)`:
```
0100 0100 >> 3 (A)
------------------
0000 1000 (bin)
0x08 (hex)
```