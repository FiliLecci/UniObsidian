>[!note] Porte logiche
>Le porte logiche sono circuiti che calcolano *funzioni*

___
## Tabella di verità
Servono a definire il comportamento delle porte logiche mettendo in relazione con una tabella gli ingressi e le relative uscite.
Visto che gli operatori logici usano un sistema binario, una tabella di verità avrà un numero di righe pari a $2^n$, con $n$ il numero di ingressi della porta.
___
## AND
Un operatore che restituisce un valore $vero$ (1) solo quando tutti gli ingressi sono $vero$.
--- start-multi-column: ID_omx5
```column-settings
Number of Columns: 2
Largest Column: standard
Border: off
```

$$
\begin{array}{c c|c}
a & b & z \\
\hline
0 & 0 & 0\\
0 & 1 & 0\\
1 & 1 & 1\\
1 & 0 & 0
\end{array}
$$


--- column-break ---

![[and_gate.png]]

--- end-multi-column
## OR
Un operatore che restituisce un valore $vero$ (1) quando almeno uno degli ingressi è $vero$.
--- start-multi-column: ID_amra
```column-settings
Number of Columns: 2
Largest Column: standard
Border: off
```

$$
\begin{array}{c c|c}
a & b & z \\
\hline
0 & 0 & 0\\
0 & 1 & 1\\
1 & 1 & 1\\
1 & 0 & 1
\end{array}
$$

--- column-break ---

![[or_gate.png]]

--- end-multi-column
## NOT
Un operatore unario che inverte il valore di verità dell'ingresso.
--- start-multi-column: ID_60lq
```column-settings
Number of Columns: 2
Largest Column: standard
Border: off
```

$$
\begin{array}{c|c}
a & z \\
\hline
0 & 1 \\
1 & 0 \\
\end{array}
$$


--- column-break ---

![[not_gate.png]]

--- end-multi-column
L'operatore not è rappresentato con un pallino che può essere piazzato sia agli ingressi che alle uscite delle porte logiche per "negare" rispettivamente un ingresso o un' uscita.
___
Per costruire circuiti più complessi è necessario però usare le porte logiche sopra descritte a cascata, collegandone quindi una dopo l'altra fino ad arrivare ai risultati finali. Questa porta l'output ad essere ritardato rispetto al momento in cui diamo gli input e ciò dipende da quante porte abbiamo usato.
Questo ritardo viene chiamato [[Ritardo della porta]].
___
## Composizione di una funzione con porte logiche
Per riportare una funzione ad un circuito formato dalle porte logiche menzionate prima, dobbiamo passare attraverso vari step:
1. Descrizione "verbale" della funzione
2. Tabella di verità
3. Espressione di algebra booleana (AND, OR, NOT)
4. Circuito
>[!example] Esempio
>1) Somma di 2 bit -> risultato, riporto
>2)
>$$
> \begin{array}{c c|c|c}
> A & B & ris & rip \\
> \hline
> 0 & 0 & 0 & 0\\
> 0 & 1 & 1 & 0\\
> 1 & 0 & 1 & 0\\
> 1 & 1 & 0 & 1\\
> \end{array}
>$$
>3) Si considerano gli '1' delle uscite e si guarda la configurazione degli ingressi. Si crea quindi una configurazione di porte tenendo conto che:
>   $AND =\ \cdot,\ OR=\ +,\ NOT=\overline{}$ e che se la porta in ingresso è $0$ va negata, altrimenti si lascia invariata.
>   $ris=(\overline A \cdot B + A \cdot \overline B)$
>   $rip=(A \cdot B)$
> 4) ![[2bit_adder.png|300]] ^173238


