# Practice 2.7

What would be printed as a result of the following call to show_bytes?

```
const char* m = "mnopqr";
show_bytes((byte_pointer) m, strlen(m));
```

Note that letters 'a' through 'z' have ASCII codes `0x61` through `0x7A`

---

Since we are given the start and end ASCII codes for a-z letters we can construct the rest of the ASCII table that will allow us to solve the problem.

```
0x61   0x62   0x63   0x64   0x65
   a      b      c      d      e

0x66   0x67   0x68   0x69   0x6A
   f      g      h      i      j

0x6B   0x6C   0x6D   0x6E   0x6F
   k      l      m      n      o

0x70   0x71   0x72   0x73   0x74
   p      q      r      s      t

0x75   0x76   0x77   0x78   0x79
   u      v      w      x      y

0x7A  
   z
```

Now we can get the ASCII character code for every lower case letter we can do the conversion noting that the `NUL` character is not included in the calculation for strlen:

```
 'm'   'n'   'o'   'p'   'q'   'r' 
0x6D  0x6E  0x6F  0x70  0x71  0x72
----------------------------------
  6D    6E    6F    70    71    72
```