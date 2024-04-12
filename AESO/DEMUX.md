>[!note] Demultiplexer
>Il demultiplexer è un componente simile al multiplexer, l'unica differenza è che ad essere scelto è l'output invece che l'input. Prende quindi in ingresso 1 solo input $a$ e $log_2n$ bit di controllo $ctl_i$ e restituisce sull'uscita definita dai bit di controllo il valore dato in ingresso.
>Le uscite che non vengono scelte sono messe a $0$.
>La dicitura DEMUX $n$x$m$ indica che abbiamo un demultiplexer con $n$ ingressi e $m$ uscite.
>>[!example] Esempio DEMUX 1x4
>>Abbiamo un demultiplexer con quattro uscite di 1 bit ciascuna. La sua tabella di verità semplificata (come fatto per il [[MUX|multiplexer]]) sarà la seguente.
>>$$
>>\begin{array}{c c c|c|c|c|c}
>>ctl_1 & ctl_2 & x & Z_1 & Z_2 & Z_3 & Z_4\\
>>\hline
>>0 & 0 & 1 & 1 & 0 & 0 & 0\\
>>0 & 1 & 1 & 0 & 1 & 0 & 0\\
>>1 & 0 & 1 & 0 & 0 & 1 & 0\\
>>1 & 1 & 1 & 0 & 0 & 0 & 1\\
>>\end{array}
>>$$

___

