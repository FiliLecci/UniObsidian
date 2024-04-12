Dato $\beta \in (0,1)$, informalmente un $\beta$-quantile (o $k\cdot\beta$ percentile) è un numero $r_\beta \in \mathbb R$ t.c.
$$F_X(r_\beta)=\mathcal P\{X\leq r_\beta\} = \beta$$
tuttavia, un tale $\beta$ può non esistere o non essere unico, prendiamo quindi una definiziome migliore:
>[!note] $\beta$-quantile
>un numero $r \in \mathcal R$ t.c.
>$$P\{X \leq r\} \geq \beta\quad e\quad P\{X\geq r\}\geq 1 - \beta$$

### Trovare un $\beta$-quantile
v.a. discrea $X$ a valori in $X-1,x_2,...$, supponiamo che non siano crescenti
1. $\nexists x_i$ t.c. $F_X(x_i) = \beta$
   $r_\beta$ = il più piccolo degli $x_i$ t.c. $F(x_i) > \beta$
2. $\exists x_i$ t.c. $F_X(x_i) = \beta$
   ogni $r\in(x_i, x_{i+1}]$ è un $\beta$-quantile, per convenzione, il [[media campionaria|punto medio]] $\frac{x_i + x_{i+1}}{2}$
___
v.a. $X$ con densità $f$:
1.  $\exists ! r_\beta$ t.c. $F_X(r_\beta) = \beta$
   $r_\beta$ è il $\beta$-quantile
2. $F_X^{-1}(\beta)$ è un intervallo
   ogni valore nell'intervallo è un $\beta$-quantile per convenzione, si prende come $\beta$-quantile l'estremo sinistro di $F_X^{-1}(\beta)$.