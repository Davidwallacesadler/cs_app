# Section 2.12 Integer Representations
This section focuses on signed and unsigned integer representations with a focus on overflow as well.

## Notes
- The section outlines "two different ways bits can be used to encode integers" (95). This is unsigned and two's complement encodings!
- "Each type can specify a size with keyword `char`, `short`, `long` as well as an indication of whether the represented numbers are all nonnegative (declared as `unsigned`) or possibly negative (the default)" (96).
- "The most common computer representation of signed numbers is known as two's-complement form... where the most significant bit is also called the sign bit" (100).
- "The two's complement range is asymmetric: |Tmin| = |Tmax| + 1 ... This asymmetry arises because half the bit patterns (those with sign bit set to 1) represent negative numbers, while half (those with sign bitt set to 0) represent non negative numbers. Since 0 is nonnegative this means we can represent one less positive number than negative" (102).
- "Two's complement arises from the fact that for nonnegative x we compute a w-bit representation of -x as 2^w - x (a single two). The term ones' complement comes from the property that we can compute -x in this notation as [111...1] - x (multiple ones)" (104).

