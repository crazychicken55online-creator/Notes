The power rule states that if $a$ is any real number and $f(x)=x^a$ then $f^-1(x)=ax^{a-1}$
# Proof
The [[Binomial Theorem]] tells us that:
$$
(a + b)^n = \sum_{k=0}^{n} \binom{n}{k} a^{n-k} b^k
$$

$$
= a^n + \binom{n}{1} a^{n-1}b + \binom{n}{2} a^{n-2}b^2 + \binom{n}{3} a^{n-3}b^3 + \cdots + \binom{n}{n-1}ab^{n-1} + \binom{n}{n}b^n
$$

$$
= a^n + n a^{n-1}b + \frac{n(n-1)}{2!}a^{n-2}b^2 + \frac{n(n-1)(n-2)}{3!}a^{n-3}b^3 + \cdots + n a b^{n-1} + b^n
$$
where,
$$\binom{n}{k}=\frac{!n}{k!(n-k)!}$$
are called the binomial coefficients and $n!=n(n-1)(n-2)\dots (2)(1)$ is the factorial.
Using this, we can prove the power rule like so:
$$
f'(x) = \lim_{h \to 0} \frac{(x + h)^n - x^n}{h}$$
$$= \lim_{h \to 0} \frac{(x^n + n x^{n-1}h + \frac{n(n-1)}{2!}x^{n-2}h^2 + \cdots + n x h^{n-1} + h^n) - x^n}{h}$$
The 2 $x^n$ will cancel out so we can factor $\frac{1}{h}$ out and evaluate the limit as we will not get a division by $0$ anymore.
$$
f'(x) = \lim_{h \to 0} \frac{n x^{n-1}h + \frac{n(n-1)}{2!}x^{n-2}h^2 + \cdots + n x h^{n-1} + h^n}{h}
$$
$$
f'(x) = \lim_{h \to 0} \left( n x^{n-1} + \frac{n(n-1)}{2!}x^{n-2}h + \cdots + n x h^{n-2} + h^{n-1} \right)
$$
$$
f'(x) = n x^{n-1}
$$
See also: [[Instantaneous Rate of Change#Formula for instantaneous rate of change|Limit definition of a derivative]].