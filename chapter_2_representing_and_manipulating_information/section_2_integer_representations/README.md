# Section 2.12 Integer Representations
This section focuses on signed and unsigned integer representations and how this relates to on overflow as well.

## Notes
- The section outlines "two different ways bits can be used to encode integers" (95). This is unsigned and two's complement encodings!
- "Each type can specify a size with keyword `char`, `short`, `long` as well as an indication of whether the represented numbers are all nonnegative (declared as `unsigned`) or possibly negative (the default)" (96).
- "The most common computer representation of signed numbers is known as two's-complement form... where the most significant bit is also called the sign bit" (100).
- "The two's complement range is asymmetric: |Tmin| = |Tmax| + 1 ... This asymmetry arises because half the bit patterns (those with sign bit set to 1) represent negative numbers, while half (those with sign bitt set to 0) represent non negative numbers. Since 0 is nonnegative this means we can represent one less positive number than negative" (102).
- "Two's complement arises from the fact that for nonnegative x we compute a w-bit representation of -x as 2^w - x (a single two). The term ones' complement comes from the property that we can compute -x in this notation as [111...1] - x (multiple ones)" (104).
- "In casting from `unsigned` to `int` the underlying bit patterns stays the same... the numeric value might chabge but the bit patterns do not." (107)
- "UMax has the same bit representation in unsigned form as does -1 in two's-complement form. We can also see the relationship between these two numbers: 1 + UMax = 2^w" (104).
- Converting from two's complement to unsigned:

`T2U(x) = x + 2^w (x < 0) or x (x >= 0)` (108)
- When converting two's complement to unsigned the positive numbers map straight accross, and negative numbers map to positive numbers because of the most significant bit. (109)
- Converting from unsigned to two's complement:

`UT2(x) = u (u <= TMax), u - 2^w (u > TMax)` (109)
- For values x in the range 0 <= x <= TMax, we have T2U(x) = x and U2T(x) = x. That is, numbers in this range have identical unsigned and two's complement representations. For values outside this range, the conversions either add or subtract 2^w" (110)
- In C "When an operation is performed where one operand is signed and the other is unsigned, C implicitly casts the signed argument to unsigned and performs the operations assuming the numbers are nonnegative". (111)

