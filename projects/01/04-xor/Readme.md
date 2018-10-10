# Xor Gate

Returns 1 when only one of the inputs are 1, otherwise 0.

```
Input: a, b
Output: out
```

## Truthtable

| a | b | out |
|---|---|-----|
| 0 | 0 |  0  |
| 1 | 0 |  1  |
| 0 | 1 |  1  |
| 1 | 1 |  0  |


## Solution 

Looking again at the truthtable for our `Nand` gate and(!) looking at the one for our `Or` gate we can see that if we combine the outputs of the two tables with an `And` gate we get the desired output.

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