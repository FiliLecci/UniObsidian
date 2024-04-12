>[!note] Multiplexer (commutatore)
>Il multiplexer è un componente che prende in ingresso $n$ input e $log_2n$ bit di controllo $ctl_i$. L'uscita $Z$ è determinata dai bit di controllo con i quali si sceglie l'input.
>Indichiamo con MUX $n$x$m$ un multiplexer con $n$ ingressi e $m$ uscite.
>>[!example] Esempio MUX 2x1
>>Abbiamo un multiplexer con due input $a$ e $b$ di 1 bit ciascuno, la sua tabella di verità sarà la seguente
>>$$
>>\begin{array}{c c c|c}
>>ctl_1 & a & b & Z\\
>>\hline
>>0 & 0 & 0 & 0\\
>>0 & 0 & 1 & 0\\
>>0 & 1 & 0 & 1\\
>>0 & 1 & 1 & 1\\
>>\hline
>>1 & 0 & 0 & 0\\
>>1 & 0 & 1 & 1\\
>>1 & 1 & 0 & 0\\
>>1 & 1 & 1 & 1\\
>>\end{array}
>>$$
>>Semplificando l'espressione logica che risulta dalla tabella di verità possiamo arrivare a capire che essa corrisponde a $\overline{ctl} \cdot a + ctl \cdot \overline a$ e cioè che in base al valore di $ctl$ si sceglie $a$ o $b$. Possiamo quindi in base al valore di $ctl$ ignorare uno dei due input, semplificando di molto la tabella di verità:
>>$$
>>\begin{array}{c c c|c}
>>ctl_1 & a & b & Z\\
>>\hline
>>0 & 0 & - & 0\\
>>0 & 1 & - & 1\\
>>\hline
>>1 & - & 0 & 0\\
>>1 & - & 1 & 1\\
>>\end{array}
>>$$

___

