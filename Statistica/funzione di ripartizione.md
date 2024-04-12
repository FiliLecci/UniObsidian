$(\Omega, \mathcal P)$ [[Statistica/spazio di probabilità]], $X:\Omega\rightarrow \mathbb R$ var. aleatoria, $P_x$ legge $P_x(A)=P(X\in A)$

>[!note] Definizione
>Funzione di ripartizione (cumulativa distribution function c.d.f) di $X$:
>$$F_X:\mathbb R \rightarrow [0,1]\ data\ da\ F_X(x) = P(X\leq x) = P_X((-\infty, x])$$

>[!warning] Osservazione
>$F_X$ dipende solo dalla legge di $X (P_X=P_y \Rightarrow F_X = F_y)$

___
### Prorietà di $F_X$
1. $F_X$ è non-decrescente
2. $\lim_{x\rightarrow-\infty} F_X(x) = 0$
   $\lim_{x\rightarrow+\infty} F_X(x) = 1$
3. $F_X$ continua a destra
>[!note] Proposizione
>Data $F: \mathbb R \rightarrow [0,1)$ che soddisfa $(a)-(b)-(c)$, allora $\exists ! Q$ prob. su $\mathbb R$ di cui $F$ sia funzione di ripartizione, cioè $F$ sia funz. di rip. di una var. aleatoria $X$ di legge $P_X = Q$.
>In particolare se $x$ e $y$ hanno la stessa funz. di ripartizione allora $P_x = P_y$

___
### Calcolo delle prob. di un intervallo a partire dalla funz. di ripartizione

- $P(a < X \leq b) = F_X(b)-F_X(a)$
Dim:
$P(a < X \leq b) = P(X\leq b) - P(X \leq a) = F_X(b)-F_X(a)$

- $P(X\leq b) = F_X(b)$
- $P(X > a) = 1 - F_X(a)$
- $P(X=a) = F_X(a)-F_X(a-)$ dove $F_X(a) = \lim_{x\rightarrow a^-} F_X(x)$
- c.d.f di v.a. $X$ discreta a valori $m\{x_1,x_2,...\}$
	  $F_X$ costante a tratti ("a gradini"), in particolare
	- $F_X$  costante tra due $x_i$ consecutivi
	- in ogni $x-i$ ha un salto di ampiezza $P_X(x_i) = P(X=x_i)$ 
- c.d.f di v.a. $X$ con densità $f$:
	- $F_X(x) = P(X\leq x) = \int^{x}_{-\infty}f(y)dy$
	  in particolare $F_X$ è continua
	- poiché $P(X=a)=0$,
	- se $F_Y$ è continua su $\mathbb R$ ed è $C^1$ a tratti, allora $y$ ammette densità $f_y = F^{'}_y$ in tutti i punti dove $F_Y$ è derivabile.