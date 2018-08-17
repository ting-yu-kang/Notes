RSA Encryption
===
### Links
* [part1](http://www.ruanyifeng.com/blog/2013/06/rsa_algorithm_part_one.html)
* [part2](http://www.ruanyifeng.com/blog/2013/07/rsa_algorithm_part_two.html)

### Euler's totient function

$$
\varphi(n) = n(1-\frac{1}{p_1})(1-\frac{1}{p_2})\dots(1-\frac{1}{p_r})
$$

### Euler's theorem
$$
a^{\varphi(n)} \equiv 1\ (\bmod\ n)
$$
if p is a prime, then
$$
a^{p-1} \equiv 1\ (\bmod\ p)
$$

### Modular multiplicative inverse
$$
ab \equiv 1 (\bmod\ n)
$$
$$
a \times a^{\varphi(n)-1} \equiv 1 \,(\bmod\ n)
$$

### RSA
#### Generate Key
1. randomly choose to primes $p,q$
2. $n = p \times q$
3. $\varphi(n) = (p-1)(q-1)$
4. randomly choose e where $1<e<\varphi(n),\ gcd(e, \varphi(n)) = 1$
5. calculate $d$ (modular multiplicative inverse of $e$)
    $$
    ed \equiv 1\ (\bmod\ \varphi(n))
    \\
    ed - k\varphi(n) = 1
    $$
    then we can get d
6. public key:$(n,e)$, private key:$(n,d)$

#### Encrypt with public key $(n,e)$ (message: $m$, send $c$)
$$
    m^e \equiv c\ (\bmod\ n)
$$
#### Decrypt with private key $(n,d)$ (receive $c$)
$$
    c^d \equiv m\ (\bmod\ n)
$$
