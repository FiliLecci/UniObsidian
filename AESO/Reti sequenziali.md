[[Latch SR]]
[[D - Latch]]
[[D - flip flop]]
___
## Automi
Un automa è qualcosa in cui gli ingressi e lo stato corrente determinano l'uscita ed il prossimo stato.
Esistono due tipi di automi:
- ***Mealy***: l'uscita dipende sia dallo **stato** che dall'**ingresso**:
  Gli archi sono etichettati con gli ingressi e le uscite.
- ***Moore***: l'uscita dipende solo dallo **stato**:
  Gli archi sono etichettati solo con gli ingressi e le uscite sono etichettate negli stati.
___
### Automa con reti sequenziali
Prendiamo come esempio il seguente automa di **Mealy**:
![[automaMealy.png|500]]
definiamo gli stati e i possibili ingressi come
$$
\begin{align}
stati &\in \{S_0, S_1, S_2\}\\
ing &\in \{a, b\}
\end{align}
$$
dove indichiamo gli stati rispettivamente con $00, 01, 10$ e gli ingressi con $0, 1$.
Possiamo rappresentare il precedente automa con due tabelle di verità, la prima che prende un input e uno stato e definisce lo stato di destinazione e l'altra che dato lo stato definisce l'output:
La dicitura $St_n$ indica l'$n$-esimo bit dello stato.
$$
\begin{array}{c c c|c c}
St_1 & St_0 & x & St_1' & St_0'\\
\hline
0 & 0 & 0 & 0 & 1\\
0 & 0 & 1 & 0 & 0\\
0 & 1 & 0 & 0 & 1\\
0 & 1 & 1 & 1 & 0\\
1 & 0 & - & 0 & 0\\
\end{array}
\Rightarrow
\begin{align}
St_1' &= \overline{St_1} \cdot St_0 \cdot x\\
St_0' &= \overline{St_1} \cdot \overline{St_0} \cdot \overline{x}+
		\overline{St_1} \cdot St_0 \cdot \overline{x}
\end{align}
$$
$$
\begin{array}{c c c|c}
St_1 & St_0 & x & Z\\
\hline
0 & 0 & - & 0\\
0 & 1 & - & 0\\
1 & 0 & 0 & 1\\
1 & 0 & 1 & 0\\
\end{array}
\Rightarrow
\begin{align}
Z = St_1 \cdot \overline{St_0} \cdot \overline x
\end{align}
$$
Queste tabelle possono essere quindi "contenute" in componenti singoli che, con l'aggiunta di un [[D - flip flop#Write enable (registro)|registro]], rendono possibile il funzionamento dell'automa.
Lo schema risultante è il seguente
![[circuitoAutomaMealy.png]]