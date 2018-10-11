# Multiplexer

Returns `a` when `sel` is 0, otherwise `b`.

```
Input: a, b, sel
Output: out
```

## Truth table

| a | b | sel | out |
|---|---|-----|-----|
| 0 | 0 |  0  |  0  |
| 1 | 0 |  0  |  1  |
| 0 | 1 |  0  |  0  |
| 1 | 1 |  0  |  1  |
| 0 | 0 |  1  |  0  |
| 1 | 0 |  1  |  0  |
| 0 | 1 |  1  |  1  |
| 1 | 1 |  1  |  1  |


## Solution 

We can think of an `And` gate as kind of switch/filter, too. Depending on the value of `b` we pass the value from `a` to `out`. If `b` is 1 the value in `a` gets passed to out, else not.

### Switch `And` Truth table

| a | b | out |
|---|---|-----|
| 0 | 0 |  0  |
| 1 | 0 |  0  |
| 0 | 1 |  0  |
| 1 | 1 |  1  |

As you can see the value from `a` only gets passed to the output when `b` has the value 1. 

With this in mind we can start constructing our gate. The `Multiplexer` returns `a` if the value of `sel` is 0, else it will return the value in `b`. So if `sel` is 0, or `Not(1)` we store the output of `a` in `c`. If `sel` is 1 we store the output of `b` in `d`. The only thing now missing is an `Or` gate to set out final output. In theory we could use an `Xor` get as well, since `c` and `d` never can be 1 at the same time.


## Implementation

```hdl
CHIP Mux {
    IN a, b, sel;
    OUT out;

    PARTS:
    Not(in=sel,out=nsel);
    And(a=a,b=nsel,out=c);
    And(a=b,b=sel,out=d);
    Or(a=c,b=d,out=out);
}
```