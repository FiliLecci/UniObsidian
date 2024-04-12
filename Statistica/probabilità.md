Per un qualsiasi evento $A$, il valore della sua probabilità $P(A)$ è il "grado di fiducia che gli diamo", ossia quanto si ritiene quel dato evento probabile.

Vi sono molte definizioni storiche per definire la probabilità, ognuna delle quali è più utile per certi tipi di eventi piuttosto che per altri.

Per i nostri modelli usiamo una definizione rigorosa di probabilità (Kolmogorov) che si basa sulle proprietà fondamentali che ogni probabilità deve avere:
>[!note] Probabilità di Kolmogorov
>Dato $\Omega\notin\varnothing$ spazio campionario, una (misura di) probabilità $P$ è una funzione
>$$
>P:\mathcal P(\Omega) = \{A\subseteq \Omega\} \rightarrow [0,1]
>$$ 
>che soddisfa:
>- $P(\Omega)=1$
>- se $A_i, i=1,2,...$ è una successione (finita o infinita) di eventi a due  due disgiunti (cioè tali che $A_i \cap A_j = \varnothing \forall i \neq j$) allora
>	1. $P(\bigcup^n_{i=1}A_i)=\sum^n_{i=1} \mathcal P(A_i)$ per una successione finita
>	2. $P(\bigcup^\infty_{i=1}A_i)=\sum^\infty_{i=1} \mathcal P(A_i) = \lim_{n\rightarrow +\infty} \sum^n_{i=1} \mathcal P(A_i)$ per una successione infinita

___

>[!warning]
>- un evento è trascurabile se $\mathcal P(A)=0$
>- un evento è quasi certo se $\mathcal P(A) = 1$

___

>[!note] Osservazione
>Uno spazio di prob. è in realtà composto da una terna del tipo $(\Omega, \mathcal F, \mathcal P)$ dove $\mathcal F$ è un insieme di eventi "ammissibili", su cui $\mathcal P$ è definita.

In generale quindi $\mathcal F$ può non essere $\mathcal P(\Omega)$ però, tutti gli insiemi "ragionevoli" sono ammissibili.
### Proprietà
```tikz
\begin{document}
\begin{tikzpicture}[fill=gray]

\draw (0,0) circle (1) (0,1)  node [text=black,above] {$A$}
      (-2,-2) rectangle (2,2) node [text=black,above] {$\Omega$}
      (1.1,1.1) node [text=black, above] {$A^c$}
      (-0.3,-0.3) circle (0.5) (-0.3,-0.5) node [text=black, above]{$B$}
      (0.4,0) node [text=black, above] {$A\backslash B$};

\end{tikzpicture}
\end{document}
```
- $\mathcal P(\Omega|B)=1$
- $\mathcal P(A^c) = 1-\mathcal P(A)$ e in particolare $\mathcal P(\emptyset) = 0$
- $B \subseteq A \Rightarrow \mathcal P(A\backslash B) = \mathcal P(A)-\mathcal P(B)$ e $\mathcal P(B) \leq \mathcal P(A)$
- $\mathcal P(A\cup B) = \mathcal P(A) + \mathcal P(B) - \mathcal P(A \cap B)$.
  dimostrazione per esercizio
  - $\mathcal P(\bigcup_i A_i|B) = \sum_i \mathcal P(A_i|B)$ per $A_i$ disgiunti
- generalizzazione a $\mathcal P(A,U,...,UA_n)$ = ... (inclusione - esclusione)
- 3.1.2