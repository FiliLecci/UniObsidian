>[!note] Definizione algoritmica
>Rappresentiamo il negativo di un numero binario ($n_2 \rightarrow -n$) effettuando 3 passi:
>- $|n_{10}| \rightarrow n_2$
>- complemento di tutti i bit di $|n|$
>- sommo $1$

>[!example] Esempio
>$$
>\begin{array}{l}
>n_{10} = -3\\
>1) & |3|_{2} = 0000\ 0011\\
>2) & 1111\ 1100\\
>3) & 1111\ 1101
>\end{array}
>$$
>Ora se proviamo a rappresentare l'operazione $-3+2$ otteniamo:
>$$
>\begin{array}{l}
>-3 & 1111\ 1101 & +\\
>+2 & 0000\ 0010 & =\\
>\hline
>-1 & 1111\ 1111\\
>\end{array}
>$$
>Possiamo applicando le regole dette sopra confermare che $-1$ è in effetti rappresentato in complemento a 2 come $1111\ 1111$.

Questa rappresentazione ha anche altre due proprietà che risultano fondamentali per la memorizzazione dei dati; quando si moltiplica o divide per una potenza di 2 è infatti sufficiente fare rispettivamente uno shift a sinistra o destra dei bit del numero.
>[!example] Esempio
>$0011 \cdot 0010 = 0110$

