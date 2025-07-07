# Practice 2.11

Armed with the function `inplace_swap` from Problem 2.10, you decide to write code that will reverse the elements of an array by swapping elements from opposite ends of the array, working toward the middle.

You arrive at the following function:

```c
void reverse_array(int a[], int cnt) {
    int first, last;
    for (first = 0, last = cnt-1; first <= last; first++, last++)
        inplace_swap(&a[first], &a[last]);
}
```

When you apply your function on an array containing elements 1, 2, 3, and 4, you find the array now has, as expected, elements 4, 3, 2, and 1. When you try it on an array with elements 1, 2, 3, 4, and 5, however, you are surprised to see that the array now has elements 5, 4, 0, 2, and 1. In fact, you discover that the code always works correctly on arrays of even length, but it sets the middle element to 0 whenever the array has odd length.

[A.](#a) For an array of odd length `cnt = 2k + 1`, what are the values of variables `first` and `last` in the final iteration of function `reverse_array`?

[B.](#b) Why does this call to function `inplace_swap` set the array element to 0?

[C.](#c) What simple modification to the code for `reverse_array` would eliminate this problem?

---

## A.

For an array of odd length `cnt = 2k + 1`, what are the values of variables `first` and `last` in the final iteration of function `reverse_array`?

We can walk through this issue by picking an example to run through the function. Suppose `a = [1, 2, 3, 4, 5]`, and `cnt = 5`.

On the first iteration:
```
first = 0
last = 4

0 <= 4 (Condition Passes)

a[0] = 1
a[4] = 5

swap(&a[0], &a[4]) 
------------------
=> [5, 2, 3, 4, 1]
```

On the second iteration:
```
first = 1
last = 3

1 <= 3 (Condition Passes)

a[1] = 2
a[3] = 4

swap(&a[1], &a[3]) 
------------------
=> [5, 4, 3, 2, 1] -- NOTE: We are done here!
```

On the third iteration:
```
first = 2
last = 2

2 <= 2 (Condition Passes)

a[2] = 2
a[2] = 2

swap(&a[2], &a[2]) 
------------------
=> [5, 4, 0, 2, 1] -- Since a ^ a = 0
```

On the fourth iteration:
```
first = 3
last = 1

3 <= 1 (Condition Fails)
```

So we can see from walking through the problem that the issue results from the loop condition. We have to make sure we don't pass the same element into `inplace_swap`!

## B.

Why does this call to function `inplace_swap` set the array element to 0?

As seen above, the 0 results from the state where `last == first`. This results in passing the same value to `inplace_swap` for both parameters. Then since we know `a ^ a = 0` it is clear that this is the cause of the 0 value.

## C.

As seen in A. we could have ended the iteration a step earlier to avoid the issue. So simply chaning the loop conditon from `first <= last` to `first < last` should do the trick.
