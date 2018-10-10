# Or Gate

Returns 1 when at least one of the inputs are 1, otherwise 0.

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
| 1 | 1 |  1  |


## Solution 

Looking at the truthtable of the `Nand` gate we can see that if any of the inputs are 0 the output is 1. The logic for our `Or` gate is inverted (or negated). Meaing for any input that is 1 the output is 1. From that we can derive our implementation.

## Implementation

```hdl
CHIP Or {
    IN a, b;
    OUT out;

    PARTS:
    Not(in=a, out=Nota);
    Not(in=b, out=Notb);
    Nand(a=Nota, b=Notb, out=out);
}
```