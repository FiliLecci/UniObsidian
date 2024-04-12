Si definisce _insieme dei numeri di macchina_ in rappresentazione floating point con $t$ cifre, base $\beta$ e range $(-m,M)$ l'insieme dei numeri reali
$$
\mathbb F(\beta,t,m,M) = \{0\} \cup \{x\in \mathbb{R}:x=sign(x)\beta^p\sum^t_{i=1}d_iB^{-i}\}\quad con
\begin{cases}
0 \leq d_i\leq \beta-1\\
d_1 \neq 0\\
-m\leq p \leq M
\end{cases}
$$
___
>[!note] Osservazioni
>- L'insieme dei numeri di macchina $\mathbb F(\beta, t, m, M)$ ha cardinalità finita $N=2B^{t-1}(B-1)(M+m+1)+1$.
>-  L'insieme dei numeri di macchina $\mathbb F(\beta, t, m, M)$ è simmetrico rispetto all'origine
 >- 
