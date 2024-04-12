Nell'intervallo $\overline{x} \longleftrightarrow x_i$, indichiamo la distanza di ogni dato $x_i$ dalla media campionaria $\overline{x}$ con $x_i-\overline{x}$.

La varianza empirica è espressa come
$$
Var_e(x)=\frac{1}{n}\sum^{n}_{i=1}(x_i-\overline{x})^2 = \left(\frac{1}{n}\sum^{n}_{i=1}x^2_i\right)-\overline{x}^2
$$
Come nel caso della [[media campionaria]], possiamo calcolare la varianza empirica con la [[frequenza#Frequenza relativa|frequenza relativa]] nel seguente modo
$$
Var_e(x)=\frac{1}{n}\sum^{m}_{j=1}a^2_jp(a_j)-\overline{x}^2 \qquad
\begin{cases}
a_j =\text{possibili esiti}\\
p(a_j)=\text{frequenza relativa di $a_j$}
\end{cases}
$$
___
>[!note] Osservazione
>Analogia con la [[covarianza e correlazione campionaria|covarianza]]:
>$$Var_e(x)=Cov(x,x)$$
