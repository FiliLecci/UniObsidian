È praticamente uguale alla [[varianza empirica]] con la sola differenza che invece di $\frac{1}{n}$ prendiamo $\frac{1}{n-1}$. Otteniamo quindi
$$
Var(x)=\frac{1}{n-1}\sum^{n}_{i=1}(x_i-\overline{x})^2 = \left(\frac{1}{n-1}\sum^{n}_{i=1}x_i^2\right)-\overline{x}^2
$$
oppure per il calcolo con frequenza relativa
$$
Var(x)=\frac{1}{n-1}\sum^{m}_{j=1}a^2_jp(a_j)-\overline{x}^2 \qquad
\begin{cases}
a_j =\text{possibili esiti}\\
p(a_j)=\text{frequenza relativa di $a_j$}
\end{cases}
$$
