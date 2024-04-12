> [!tip] Teorema
> Se $\overline{x}$ e $\overline{y}$ sono soluzioni ammissibili per $(P)$ e $(D)$ rispettivamente, allora $c\overline{x} \leq \overline{y}b$.
#### Dimostrazione
#### Da problema primale a duale
Per trovare il duale di un problema primale possiamo applicare le seguenti regole:
$$
\begin{align}
i)\quad & max\sum^{n}_{j=1} c_jx_j & \equiv &-min\sum^{n}_{j=1}(-c_j)x_j\\
ii)\quad & \sum^{n}_{j=1} a_{ij}x_j = b_j & \equiv & \left\{\begin{array}{rl}
\sum^{n}_{j=1}a_{ij}x_j & \leq b_i\\
\sum^{n}_{j=1}a_{ij}x_j & \geq b_i
\end{array}\right.\\
iii)\quad & \sum^{n}_{j=1}a_{ij}x_j \geq b_i & \equiv & \sum^{n}_{j=1}(-a_{ij})x_j \leq -b_i\\
iv)\quad & \sum^{n}_{j=1}a_{ij}x_j\geq b_i & \equiv & \sum^{n}_{j=1}a_{ij}x_j-s_i = b_i,\ s_i \geq 0\\
v)\quad & \sum^{n}_{j=1}a_{ij}x_j\leq b_i & \equiv & \sum^{n}_{j=1}a_{ij}x_j+s_i = b_i,\ s_i \geq 0\\
\end{align}
$$
