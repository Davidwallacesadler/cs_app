# Practice 2.5

Consider the following three calls to `show_bytes`:

```
typedef unsigned char* byte_pointer;
void show_bytes(byte_pointer start, size_t len);

int a = 0x12345678;
byte_pointer ap = (byte_pointer) &a;
show_bytes(ap, 1); /* A */
show_bytes(ap, 2); /* B */
show_bytes(ap, 3); /* C */
```

Indicate the values that will be printed by each call on a little-endian machine and on a big-endian machine:

[A.](#a) Little Endian ____ , Big Endian ____

[B.](#b) Little Endian ____ , Big Endian ____

[C.](#c) Little Endian ____ , Big Endian ____

---

## A.

`show_bytes(ap, 1);`

Little Endian - To read this we start on the right and take each byte (each two hex character grouping) in the same order L to R:
```
hex:      0x  1  2  3  4  5  6  7  8
byte num:     4     3     2     1    
------------------------------------
=> 0x78
```

Big Endian - We just read the hex values from L to R:
```
hex:      0x  1  2  3  4  5  6  7  8
byte num:     1     2     3     4    
------------------------------------
=> 0x12
```

## B.

`show_bytes(ap, 2);`

Little Endian:
```
hex:      0x  1  2  3  4  5  6  7  8
byte num:     4     3     2     1    
------------------------------------
=> 0x7856
```

Big Endian:
```
hex:      0x  1  2  3  4  5  6  7  8
byte num:     1     2     3     4    
------------------------------------
=> 0x1234
```

## C.

`show_bytes(ap, 3);`

Little Endian:
```
hex:      0x  1  2  3  4  5  6  7  8
byte num:     4     3     2     1    
------------------------------------
=> 0x785634
```

Big Endian:
```
hex:      0x  1  2  3  4  5  6  7  8
byte num:     1     2     3     4    
------------------------------------
=> 0x123456
```