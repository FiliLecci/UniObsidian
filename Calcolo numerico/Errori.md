Rappresentare un numero reale non nullo $x\in \mathbb R, x\neq 0$, in macchina significa approssimare $x$ con un numero $\tilde{x} \in \mathbb F(\beta, t, m, M)$ commettendo un ***errore relativo*** di rappresentazione
$$
\epsilon_x = \frac{\tilde x - x}{x} = \frac{\eta_x}{x}, \quad x\neq 0
$$
quanto più piccolo possibile in valore assoluto (più è piccolo $|\epsilon _x|$ meglio è).
La quantità
$$\eta_x = \tilde x - x$$ è detta ***errore assoluto*** di rappresentazione.
___
### Errore assoluto vs errore relativo
L'errore relativo è importante e utile per dare una valutazione *qualitativa* del fenomeno considerato, al contrario l'errore assoluto assume significato e rilevanza diversi in base al fenomeno a cui fa riferimento.
>[!example] Esempio
>Assumiamo di avere un errore assoluto di $1cm$, questo errore assume pesi diversi in base a se si parla della misura di un tavolo oppure di distanze astronomiche.
>Se misuriamo un tavolo di $150cm$ l'errore relativo sarà di $\epsilon _x = \frac{\tilde x -x}{150}$ mentre per una misura astronomica di $1ua$ è $\epsilon _x = \frac{\tilde x -x}{1,496e+13}$.

