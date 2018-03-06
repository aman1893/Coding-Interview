## Number Theory

### GCD (iterative)
While writing code just assume ```a >= b```. If b is greater than a, then the numbers will automatically reverse after the first iteration.

```c++
int gcd (int a, int b) {
    while (b) {
        a %= b;
        swap (a, b);
    }
    return a;
}
```

### LCM
We can use the gcd function above to calculate the LCM.  
>We are dividing a by gcd first to avoid int overflow in the case when LCM lies in the int range but (a * b) can exceeds the int range.  

```c++
int lcm (int a, int b) {
    return a / gcd (a, b) * b;
}
```

### Extended Euclidean algorithm
It computes, in addition to the greatest common divisor of integers a and b, also the coefficients of Bézout's identity, which are integers x and y such that
ax + by = gcd(a,b)  
  
a and b are computed recursively. We can write them in terms of coefficients of the numbers in the next iteration.  
Next iteration: (b%a)x1 + ay1 = gcd(a,b)

Then x and y can be expressed in terms of x1 and y1 and can be calculated recursively.

```
x = y1 - (b/a)*x1
y = x1
```

[Emaxx Algo link](https://e-maxx.ru/algo/extended_euclid_algorithm)

```c++
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

### a^n mod m

```
int binpow (int a, int n, int m) {
    int res = 1;
    while (n) {
        if (n & 1)
            res = (1LL * res * a) % m;
        a = (1LL * a * a) % m;
        n >>= 1;
    }
    return res;
}
```









