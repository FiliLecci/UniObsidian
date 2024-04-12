> [!note] Definizione
> Dato $(\Omega, \mathcal P)$ spazio di probabilità, $B$ evento non trascurabile ($\mathcal P(B)>0$), $A$ evento, si chiama probabilità condizionata di $A$ dato $B$
> $$\mathcal P(A | B) := \frac{\mathcal P(A \cap B)}{\mathcal P(B)}$$
> cioè la probabilità che si verifichi $A$, sapendo che si verifica $B$

>[!example] Esempio
>Supponiamo di lanciare un dado equilibrato del quale sappiamo che l'esito è pari.
>Quale è la probabilità che l'esito sia $\geq 4$?
>$A = \{esiti \geq 4\}=\{4,5,6\} \qquad B=\{pari\}=\{2,4,6\}$
>allora
>$$
>\frac{2}{3} 
>= \frac{\#\{esiti\ pari\geq4\}}{\#\{pari\}} 
>= \frac{\#(A \cap B)}{\# B}
>= \frac{\frac{\#(A \cap B)}{\# \Omega}}{\frac{\#B}{\#\Omega}}
>= \frac{\mathcal P(A \cap B)}{\mathcal P(B)}
>$$
