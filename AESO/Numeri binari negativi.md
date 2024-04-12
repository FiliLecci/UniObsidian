>[!note] Range numeri negativi
> Per un dato numero di bit $n$, possiamo rappresentare numeri da $-2^{n-1}$ a $2^{n-1}$

___
Per i numeri binari negativi incontriamo un problema riguardante il modulo ed il segno di questi. Per rappresentarli usando una notazione basilare dove il primo bit è il segno ed il resto è il modulo, rappresentare $-0$ e $0$ significa avere due rappresentazioni per lo stesso numero, ossia $10000$ e $00000$.
Questo implica che nell'andare a comparare due numeri, siccome si fa un AND logico, questi due risulteranno come due numeri diversi ed è quindi necessario comparare il valore assoluto di essi che altro non rappresenta che uno spreco di risorse.
Anche nell'andare ad effettuare operazioni di somma o sottrazione, il circuito che ne risulta dovrebbe "ragionare" molto sui segni e nel caso di segni inversi cambiare l'operazione da fare.
Per ovviare a queste problematiche si usa il [[Complemento a 2]].
___