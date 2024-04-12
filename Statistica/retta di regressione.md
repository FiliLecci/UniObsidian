La retta di regressione è la retta che meglio approssima i dati $(x_i,y_i)$

Ricordando che una retta viene nella forma
$$y=a+bx$$
cerchiamo $a,b$ in modo da minimizzare le distanze tra $y_i$ e $a+bx$.
$$min_{a,b \in \mathbb R}\left(\sum^n_{i=1}(y_i-a-bx_i)^2\right) \qquad (*)$$ ^f4334d
> [!caution] Teorema
> Supponiamo $\sigma(x) \neq 0$, $\sigma(y) \neq 0$:
> il minimo del [[retta di regressione#^f4334d|problema]] $(*)$ si ottiene per
> $$
> b = b^* := \frac{Cov(x,y)}{Var(x)} \qquad a = a^* = -b^*\overline{x}+\overline{y}
> $$
> e vale
> $$
> min_{a,b\in\mathbb R}\sum^n_{i=1}(y_i-a-bx_i)^2 = (n-1)\cdot Var(y) \cdot (1-r(x,y)^2)
> $$
> >[!note] Def:
> >La retta $y=a^*+b^*x$ è detta retta di regressione tra x e y
#### Spiegazione
La distanza del punto $(x_i, y_i)$ dalla retta $y=a+bx$ è definita da $d=|y_i-(a+bx_i)|$.

Per eliminare il valore assoluto che dà più problemi che altro, prendiamo direttamente il quadrato $d^2=(y_i-a-bx_i)^2$.

Ora che sappiamo come calcolare la distanza di ogni punto dalla retta, le sommiamo.

La retta di regressione è la retta che ha distanza media dai dati minore rispetto ad una qualsiasi altra retta, quindi non ci resta che minimizzare la media delle distanza per $a,b\in \mathbb R$, tuttavia, per un $n$ fissato minimizzare la media delle distanze oppure minimizzare la somma delle distanze non fa alcuna differenza. Prendiamo quindi come valore da minimizzare la somma delle distanze.

La bontà dell'approx è tanto migliore quanto più è piccolo il min., cioè quanto più il coeff. di correlazione $r$ è vicino a $\pm 1$. In particolare, $r=\pm 1$ = il min in (\*) è 0 $\Rightarrow$ tutti i punti $(x_i,y_i)$ giacciono su una retta.
Il segno di $r$ coincide con il segno di $b^*$.
Se invece $r\approx 0$ allora i dati non sono approssimabili da alcuna relazione lineare, ciò non esclude però che ci sia un altro tipo di relazione (ad es. quadratica). 