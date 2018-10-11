# Xor Gate

Returns 1 when its two inputs have opposing values, otherwise 0.

```
Input: a, b
Output: out
```

## Truth table

| a | b | out |
|---|---|-----|
| 0 | 0 |  0  |
| 1 | 0 |  1  |
| 0 | 1 |  1  |
| 1 | 1 |  0  |


## Solution 

Looking again at the Truth table for our `Nand` gate and(!) looking at the one for our `Or` gate we can see that if we combine the outputs of the two tables with an `And` gate we get the desired output.

## Implementation

```hdl
CHIP Xor {
    IN a, b;
    OUT out;

    PARTS:
    Nand(a=a, b=b, out=aNandb);
    Or(a=a, b=b, out=aOrb)
    And(a=aNandb, b=aOrb, out=out)
}
```