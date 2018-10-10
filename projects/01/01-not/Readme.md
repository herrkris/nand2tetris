# Not Gate

Converts from 0 to 1 and from 1 to 0.

```
Input: in
Output: out
```

## Solution 

Assuming our most basic gate is the `Nand` gate, deriving our `Not` gate from that is not very difficult. Since the `Nand` gate has two inputs we feed our single input to both of the `Nand` inputs.

## Implementation

```hdl
CHIP Not {
    IN in;
    OUT out;

    PARTS:
    Nand(a=in, b=in, out=out);
}
```