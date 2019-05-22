## Asymptotic notation
### Lower bound $\Omega$ (omega)
- Meaning: The running time is at least
- E.g.: $42\log{}n +\sqrt{n}+n^{1/3} = \Omega(n^{1/3}) $

### Tight bound $\Theta$ (theta)

- *Tight bound* because we've nailed the running time to within a constant factor above and below.
- E.g.: $2^{n+2} = \Theta(2^n)$ 
- E.g.: $2^{2n}=2^n*2^n= \Theta(2^{2n})$

### Upper bound big-$O$ 

- Meaning: the running time grows at most this much, but it could grow more slowly
- E.g.: $2\log{}^2n = O(n)$

## Ordering by slowest to fastest growing:

1. $\Theta(1)$
2. $\Theta(\log_2 n)$
3. $\Theta(n)$
4. $\Theta(n \log_2 n)$
5. $\Theta(n^2)$
6. $\Theta(n^2 \log_2 n)$
7. $\Theta(n^3)$
8. $\Theta(2^n)$
9. $\Theta(n!)$

