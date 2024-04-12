>[!note] Ritardo
>Assume un valore convenzionale $\Delta t$ che rappresenta simbolicamente il tempo che intercorre tra quando viene dato l'input e quando viene restituito l'output dalla porta.

--- start-multi-column: ID_bxnl
```column-settings
Number of Columns: 2
Largest Column: standard
Border: off
Column Spacing: 0px
```

>[!warning] Rapporto ritardo/n° di ingressi
>Il rapporto tra il ritardo della porta e il numero degli ingressi della porta stessa si comporta in un modo particolare; fino ad un certo numero di porte, che per convenzione è $8$, il ritardo rimane più o meno in un range che varia di pochi *picosecondi* ($1\cdot10^{-12}$ secondi) poi, superato quel numero, il ritardo ha una crescita esponenziale. Questo implica che se abbiamo un ingresso che richiederebbe un numero di ingressi maggiore di $8$, avremo bisogno di costruire un albero ottale per dividere questi ingressi in più porte con meno ingressi.

--- column-break ---

```tikz
\usepackage{pgfplots}
\begin{document}
\begin{tikzpicture}
  \begin{axis} [axis lines=left,xlabel={Ritardo $\Delta$t}, ylabel={N° ingressi}]
    \addplot [domain=0:9, smooth, thick] { 8^x };
	\addplot[thick, samples=50, smooth,domain=0:6,blue] coordinates {(8,0)(8,11^7.8)};
  \end{axis}
\end{tikzpicture}
\end{document}
```
--- end-multi-column

___

>[!example] Esempio
>Se consideriamo come esempio il circuito che [[Porte logiche#^173238|somma due bit]] vediamo che il circuito risultante è a due livelli. Possiamo quindi dire che il circuito calcola il risultato in $2\Delta t$.

