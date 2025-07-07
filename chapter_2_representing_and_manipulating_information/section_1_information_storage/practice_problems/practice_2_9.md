# Practice 2.9

Computers generate color pictures on a video screen or liquid crystal display by mixing three different colors of lights: red, green, and blue. Imagine a simple scheme, with three different lights, each of which can be turned on or off, projecting onto a glass screen.

```
Light  Screen  
R      |
 \     |
  \    |       Observer
G -----|       (>
  /    |
 /     |
B      |
```

We can then create eight different colors based on the abssence (0) or presence (1) of light sources R, G, and B:

| R | G | B | Color |
| - | - | - | ------ |
| 0 | 0 | 0 | Black  |
| 0 | 0 | 1 | Blue   |
| 0 | 1 | 0 | Green  |
| 0 | 1 | 1 | Cyan   |
| 1 | 0 | 0 | Red    |
| 1 | 0 | 1 | Magenta|
| 1 | 1 | 0 | Yellow |
| 1 | 1 | 1 | White  |

Each of these colors can be represented as a bit vector of length 3, and we can apply Boolean operations to them.

[A.](#a) The complement of a color is formed by turning off the lights that are on and turning on the lights that are off. What would be the complement of each of the eight colors listed above?

[B.](#b) Describe the effect of applying Boolean operations on the following colors:

Blue | Green = _____

Yellow & Cyan = _____

Red ^ Magenta = _____

---

## A.

To determine the complement we just flip all bits in vectors defined in the table above:

```
Black [000]   ---> White [111]
Blue [001]    ---> Yellow [110] 
Green [010]   ---> Magenta [101] 
Cyan [011]    ---> Red [100] 
Red [100]     ---> Cyan [011] 
Magenta [101] ---> Green [010] 
Yellow [110]  ---> Blue [001] 
White [111]   ---> Black [000] 
```

## B.

We apply simple Boolean operations to the bit vectors for each color:

Blue | Green = _____

```
Blue = [001], Green = [010]
=> 001
   010 |
   -----
   011 (Cyan)
```

Yellow & Cyan = _____

```
Yellow = [110], Cyan = [011]
=> 110
   011 &
   -----
   010 (Green)
```

Red ^ Magenta = _____

```
Red = [100], Magenta = [101]
=> 100
   101 ^
   -----
   001 (Blue)
```
