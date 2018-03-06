## Number Theory

### GCD (iterative)

```C++
int gcd (int a, int b) {
    while (b) {
        a %= b;
        swap (a, b);
    }
    return a;
}
```

### LCM

```C++
int lcm (int a, int b) {
    return a / gcd (a, b) * b;
}
```

### Euclid's Extended GCD
If g is the GCD of a and b, there exists x & y such that the below condition holds:
ax + by = g
Next Iteration: (b%a)x1 + ay1 = g

Then x and y can be expressed in terms of x1 and y1 and can be calculated recursively.

```
x = y1 - (b/a)*x1
y = x1
```

```C++
int gcd (int a, int b, int & x, int & y) {
    if (a == 0) {
        x = 0; y = 1;
        return b;
    }
    int x1, y1;
    int d = gcd (b%a, a, x1, y1);
    x = y1 - (b / a) * x1;
    y = x1;
    return d;
}
```









