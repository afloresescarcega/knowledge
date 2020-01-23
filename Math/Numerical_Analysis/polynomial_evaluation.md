When evaluating polynomial expressions, a few ways may be used to evaulate them. Below, these methods range in efficiency measured by count of operations. 

Ex.
p(x) = 2x^4 + 3x^3 - 3x^2 + 5x - 1

Question: evaulate at x = 1/2

### Naïve approach (plug-in)
p((.5)) = 2(.5)^4 + 3(.5)^3 - 3(.5)^2 + 5(.5) - 1

Operations extended:
p((.5)) = 2(.5)(.5)(.5)(.5) + 3(.5)(.5)(.5) - 3(.5)(.5) + 5(.5) - 1

| Multiplications | Additions |   |   |   |
|-----------------|-----------|---|---|---|
| 10              | 4         |   |   |   |
|                 |           |   |   |   |
|                 |           |   |   |   |

Total: 14 operations or N(N+3)/2


### Approach 2: Save powers

```python
prod2 = .5 * .5
prod3 = prod2 * .5
prod4 = prod3 * .5
```

When you substitute the saves powers for x,
`p(x) = 2*prod4 + 3*prod3 - 3*prod2 + 5x - 1`

| Multiplications | Additions |   |   |   |
|-----------------|-----------|---|---|---|
| 7               | 4         |   |   |   |
|                 |           |   |   |   |
|                 |           |   |   |   |

Total: 11 operations or 3N - 1


### Aproach 3: Horner's method (Nested)
p(x) = 2x^4 + 3x^3 - 3x^2 + 5x - 1

	= x(2x^3 + 3x^2 - 3x + 5) - 1
	= x(x(2x^2 + 3x^1 - 3) + 5) - 1
	= x(x(x(2x + 3)- 3) + 5) - 1

| Multiplications | Additions |   |   |   |
|-----------------|-----------|---|---|---|
| 4               | 4         |   |   |   |
|                 |           |   |   |   |
|                 |           |   |   |   |

Total: 8 or 2N
### General Algorithm

p(x) = Sum from n = 0 to N of C_n * x^n


### C++ implementation

```c++
double nest(const int N, double c[], const double x){
	double p = c[N];
	for(int i = N - 1; i >= 0; --i){
		p = p * x + c[i];
	}
	return p;
}
```

