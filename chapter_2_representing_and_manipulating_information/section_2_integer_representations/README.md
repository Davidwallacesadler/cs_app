# Section 2.2
This section focuses on signed and unsigned integer representations and how this relates to on overflow as well.

# 2.2: Integer Representations
The section outlines "two different ways bits can be used to encode integers" (95). This is unsigned and two's complement encodings!

## 2.2.1: Integral Data Types
"Each type can specify a size with keyword `char`, `short`, `long` as well as an indication of whether the represented numbers are all nonnegative (declared as `unsigned`) or possibly negative (the default)" (96).

## 2.2.3: Two's Complement Encodings
"The most common computer representation of signed numbers is known as two's-complement form... where the most significant bit is also called the sign bit" (100).

"The two's complement range is asymmetric: |Tmin| = |Tmax| + 1 ... This asymmetry arises because half the bit patterns (those with sign bit set to 1) represent negative numbers, while half (those with sign bitt set to 0) represent non negative numbers. Since 0 is nonnegative this means we can represent one less positive number than negative" (102).

"Two's complement arises from the fact that for nonnegative x we compute a w-bit representation of -x as 2^w - x (a single two). The term ones' complement comes from the property that we can compute -x in this notation as [111...1] - x (multiple ones)" (104).

"In casting from `unsigned` to `int` the underlying bit patterns stays the same... the numeric value might chabge but the bit patterns do not." (107)

"UMax has the same bit representation in unsigned form as does -1 in two's-complement form. We can also see the relationship between these two numbers: 1 + UMax = 2^w" (104).

## 2.2.4: Conversions between Signed and Unsigned
Converting from two's complement to unsigned:
`T2U(x) = x + 2^w (x < 0) or x (x >= 0)` (108)

When converting two's complement to unsigned the positive numbers map straight accross, and negative numbers map to positive numbers because of the most significant bit. (109)

Converting from unsigned to two's complement:
`UT2(x) = u (u <= TMax), u - 2^w (u > TMax)` (109)

For values x in the range 0 <= x <= TMax, we have T2U(x) = x and U2T(x) = x. That is, numbers in this range have identical unsigned and two's complement representations. For values outside this range, the conversions either add or subtract 2^w" (110)

In C "When an operation is performed where one operand is signed and the other is unsigned, C implicitly casts the signed argument to unsigned and performs the operations assuming the numbers are nonnegative". (111)

## 2.2.6: Expanding the Bit Representation of a Number

"To convert a unsigned number to a larger data type, we can simply add leading zeros to the representation: this operation is known as *zero extension*." (113) So we pad with zeros to make the number bigger for the new larger type.

"For converting a two's complement number to a larger data type, the rule is to perform *sign extension*, adding copies of the most significant bit to the representation." (113) Sounds very similar to the arithmetic shift!

## 2.2.7: Truncating Numbers

"When truncating a w-bit number to a k-bit number, we drop the high-order (w-k) bits." (117) We pretty much just chop off the higher order bits when truncating to a lower bit number. This makes truncating unsigned numbers really simple!

"A Similar property holds for truncating a two's-complement number, except that it then converts the most significant bit into a sign bit" (117) So trunctating a signed integer works pretty much the same as unsigned but we need to pay attention to the MSB after performing the truncation. Essentially, we truncate as an unsigned number and then apply U2T.

"Casting of signed to unsigned leads to some non-intuitive behavior". (119) Be very careful with implicit casting and keep a mental model of whether you are working with unsigned or two's-complement integers.

"Unsigned values are very useful when we want to think of words as just collections of bits with no numeric representation" (120). This makes sense, We typically use these values for flags, enum ordinals, addresses, and sizes.

# 2.3: Integer Arithmetic
This section breaks down the "nuances of computer arithmetic" so we can write more reliable code when working with integers!

## 2.3.1: Unsigned Addition

"We cannot place any bound on the word size required to fully represent the results of arithmetic operations." (121) We always havet he possibility of overflowing and requiring a larger word size to represent the arithmetic result.

"The operation +(u/w)... can be characterized as a form of modular arithmetic, computing the sum modulo 2^w by simply discarding any bits with weight greater than 2^(w-1) in the bit-level representation of x + y." (121) So when we overflow with unsigned addition, we take the resulting bit-level representation of the sum and discard bits greater than original word size.

"[With unsigned integers] the overflow case has the effect of decrementing the su, by 2^w." (123) We are essentially "chopping off" the overflow bit(s). The overflow acts almost like a "reset" mod 2^w. This makes sense because modulo essentially clamps the values between 0 and 2^w.

"An arithmetic operation is said to *overflow* when the full integer result cannot fit within the word size limits of the data type." (123) This makes sense. Overflow just means we cannot represent the result in the current word size -- it's too big to be encoded into this amount of data!

To detect overflow of unsigned addition: "The computation of *s* (x + y, x, y >= 0) overflowed if and only if s < x (or equivalently, s < y)" (124). We can extend this to thinking about additive inverses! If we have an unsigned integer and add another one that gets us to overflow back to zero (2^w - x) and that is the definition of an additive inverse! Super cool!

## 2.3.2 Two's Complement Addition

"When the sum x + y exceeds TMax we say that a *positive overflow* has ocurred" (126). This makes sense based on what we just learned in the previous section when dealing with unsigned integers. If the new value is too big to be represented by the max value of a two's complement integer in the word size we rollover back to zero.

"When the sum of x + y is less than Tmin we say that a *negative overflow* has ocurred" (126). Again, this makes sense based on "rolling over" back to zero.

"Since two's complement addition has the exact same bit level representation, we can characterize the operation +(t/w) as one of converting the arguments to unsigned, performing unsigned addition, and then converting to two's complement" (126). So to add two two's complement integers, we pretty much just add them the same as unsigned numbers and then interpret the result as a two's complement integer. 

^ This feels like a similar approach to how we handled truncation where we would just perform the operation as usual and then handle "chopping bits" on the result after.

"For x and y in the range Tmin <= x, y <= Tmax, let s = x +(t/w) y. Then the computation of s has had a positive overflow if and only if x > 0 and y > 0 but s <= 0. The computation has had negative overflow if and only if x < 0 and y < 0 but s >= 0." (128) This makes sense! If we were adding two numbers of the same sign and the result has a different one we know we overflowed!

Positive Overflow: 
    1. x + y > Tmax
    2. x > 0 and y > 0 and x + y <= 0

Negative Overflow:
    1. x + y < Tmin
    2. x < 0 and y < 0 and x + y >= 0

## 2.3.3 Two's Complement Negation

An addititive inverse for a number x is another number -x such that when added the resulting sum is 0.

Every number x in the range Tmin_w <= x <= Tmax_w has an additive inverse under +(t/w) which we denote -(t/w)x. We can define -(t/w)x using the following piecewise function (see 131):

```
           | Tmin_w  x = Tmin_w 
-(t/w)x = <|
           | -x      x > Tmin_w
```

So Tmin_w is its own additive inverse -- we can see this pretty clearly with 4-bit word size example:

Given `w = 4`, we have Tmin_w = -8 = 1000. Adding it to itself, we see the operation overflows out of the word size (s = 10000) so using two's complement addition +(t/w) we end up with 0 since we truncate the sum to 4 bits and interpret it as a Two's complement integer - so by definition Tmin_w is its own additive inverse!

Basically: The smallest value (greatest negative value) is its own additive inverse, otherwise the value is its own additive inverse.

### Negating a Two's Complement Number

There are two ways of negating a two's complement integer outlined in the chapter:
1. Complement the bits (negate them), then increment the result (add 1)

Let's test this on a couple values with a 4-bit word size:

Tmin_4:
- Tmin_4 = -8 = 0b1000
- -(-8) = ~(0b1000) + 0b1 = 0b0111 + 0b1 = 0b1000 (as expected since Tmin is its own additive inverse)

Tmax_4:
- Tmax_4 = 7 = 0b0111
- -7 = ~(0b0111) +0b1 = 0b1000 + 0b1 = 0b1001 = -8 + 1 = -7 (as expected)

2:
- 2 = 0b0010
- -2 = ~(0b0010) + 0b1 = 0b1101 + 0b1 = 0b1110 = -8 + 4 + 2 = -2 (as expected)

0:
- 0 = 0b0000
- -0 = ~(0b0000) + 0b1 = 0b1111 + 0b1 = 0b0000 = 0 (positive overflow back to 0)

2. Split the bit vector into two bu splitting at the rightmost 1 (note as position `k`), then complement the bits to the left of position `k`.

Examples (this time writing bits as bit-vectors instead of with the `0b` prefix):

Tmin_4:
- Tmin_4 = -8 = [1000]
- -(-8) = [] [1000] (split at k = 3 - max index) = ~[] [1000] = [1000] (as expected)

Tmax_4:
- Tmax_4 = 7 = [0111]
- -7 = [011] [1] (split at k = 0) = ~[011] [1] = [] = [100] [1] = [1001] = -7 (as expected)

2:
- 2 = [0010]
- -2 = [00] [10] (split at k = 1) = ~[00] [10] = [11] [10] = [1110] = -2 (as expected) 

0:
- 0 = [0000]
- -0 = [] [0000] (split at k = 0 - min index) = ~[] [0000] = [0000] = 0 (as expected)

## 2.3.4 Unsigned Multiplication

Unsigned multiplication in C is defined to yield the *w*-bit value given by the low-order *w* bits of the 2w-bit integer product. (132)

So to multiply two unsigned integers we just multiply and then truncate to the word size.

*(u/w):
1. Multiply the integers
2. Truncate to the word size

## 2.3.5 Two's Complement Multiplication

Signed multiplication in C generally is performed by truncating the 2w-but product to w bits. (133)

*(t/w):
1. Multiply the integers
2. Truncate to the word size
3. Interpret the unsigned result as Two's Complement (U2T)

**NOTE:** As we can see from the above definitions of *(u/w) and *(t/w) the bit-level representation of both truncated products is identical for both unsigned and two's complement multiplication, even though the full representations may differ

**PROCEDURE:** It seems from the examples in this section, the way to approach multiplcation is:
1. Interpret the bits as a decimal integer
2. Perform the multiplcation
3. Interpret the product as binary
4. Truncate to the word size