>[!note] Definizione
>$n$ prove ripetute in cui ciascuna prova ha esito ***successo*** o ***insuccesso***.

$$\Omega = \{(a_1,...,a_n)|a_i\in\{0,1\}\} = \{0,1\}^n \qquad con\ \left\{ \begin{array}{l}
1=successo\\
0=insuccesso
\end{array}\right.$$
$p$ = probabilità di successo nella singola prova
$$\begin{align}
\mathcal P\{(a_i,...,a_n)\} &= \underbrace{\mathcal P\{a_1\ al\ 1°\}}_{\begin{array}{l}p\ se\ a_1=1\\1-p\ se\ a_1=0\end{array}} \cdot \mathcal P\{a_2\ al\ 2°\} \cdot ... \cdot \mathcal P\{a_n\ all'\ n°\}\\
&= p^{n°\ di\ successi} \cdot (1-p)^{n°\ di\ insuccessi}\\
&= p^{\sum^n_{i=1}a_i} \cdot (1-p)^{n-\sum^n_{i=1}a_i}
\end{align}
$$

___

