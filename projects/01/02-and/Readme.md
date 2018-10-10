# And Gate

Returns 1 when both inputs are 1, otherwise 0.

```
Input: a, b
Output: out
```

## Solution 
Using the `Nand` and `Not` gate in combination we can negate the "not" part of the `Nand` and turn it into an `And`.

## Implementation

```hdl
CHIP And {
    IN a, b;
    OUT out;

    PARTS:
    Nand(a=a, b=b, out=Nandab);
    Not(in=Nandab, out=out);
}
```