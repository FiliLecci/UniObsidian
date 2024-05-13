## Automi
Un automa è qualcosa in cui gli ingressi e lo stato corrente determinano l'uscita ed il prossimo stato.
Esistono due tipi di automi:
- ***Mealy***: l'uscita dipende sia dallo **stato** che dall'**ingresso**:
  Gli archi sono etichettati con gli ingressi e le uscite.
- ***Moore***: l'uscita dipende solo dallo **stato**:
  Gli archi sono etichettati solo con gli ingressi e le uscite sono etichettate negli stati.
___
### Automa di Mealy con reti sequenziali
Prendiamo il seguente automa di **Mealy**:
![[automaMealy.png|500]]
definiamo gli stati e i possibili ingressi come
$$
\begin{align}
stati &\in \{S_0, S_1, S_2\}\\
x &\in \{a, b\}
\end{align}
$$
dove indichiamo gli stati rispettivamente con il numero binario corrispondente alla posizione nell'insieme ($S_0 = 00, S_1=01, ecc.$ e $a=0, b=1$).
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
Si assume che all'inizio tutto sia inizializzato a 0, ma nella realtà solitamente si trova un pulsante che permette di resettare tutto.
Lo schema risultante è il seguente
![[circuitoAutomaMealy.png]]
dove $S'$ è il componente che calcola il prossimo stato, mentre $Z$ è il componente che calcola il valore di uscita.
#### Codice verilog
```verilog
// modulo per registro dello stato
module rstato(output [1:0]z, input clock, input [1:0]inval);
	reg [1:0] stato;

	initial
		begin
			stato <= 2'b00;
		end

	// quando il clock è alto memorizza il valore in ingresso
	always @(posedge clock)
		begin
			stato <= inval;
		end

	assign
		z = stato;
endmodule

// modulo calcolo dello stato in base alla tabella di verità sopra
module prosimostato(output [1:0]s, input [1:0]old, input x);
	assign s[1] = !old[1] && old[0] && x;
	assign s[0] = !old[1] && !x;
endmodule

// modulo per calcolo delle uscite
module uscite(output z, input [1:0]s, input x);
	assign z =s[1] && !s[0] && !x;
endmodule

// finite state machine
module fsm(output Z, input x, input clock);
	wire s12r; // da S' a R
	wire r2z;  // da R a Z

	S1 prossimostato(s12r, x, r2z);
	Z uscite(Z, x, r2z);
	reg rstato (r2z, s12r, 1, clock);
endmodule
```
___
### Automa di Moore con reti sequenziali
Prendiamo il seguente automa di **Moore**
![[automaMoore.png]]
definiamo gli stati e gli ingressi come
$$
\begin{align}
S &= \{S_0, S_1, S_2,S_3\}\\
x &= \{a, b\}
\end{align}
$$
con la stessa dicitura di cui l'esempio precedente.
Definiamo le tabelle di verità per gli stati e per l'output
$$
\begin{array}{c c c|c c}
St_1 & St_0 & x & St_1' & St_0'\\
\hline
0 & 0 & 0 & 0 & 1\\
&& 1 & 0 & 0\\
0 & 1 & 0 & 0 & 1\\
&& 1 & 1 & 0\\
1 & 0 & 0 & 1 & 1\\
&& 1 & 0 & 0\\
1 & 1 & 0 & 0 & 1\\
&& 1 & 0 & 0\\
\end{array}
\Rightarrow
\begin{align}
St_1' = &\overline{St_1} \cdot St_0 \cdot \overline{x} + St_1 \cdot \overline{St_0} \cdot \overline{x}\\
St_0' = &\overline{St_1 \cdot St_0 \cdot x} + \overline{St_1} \cdot St_0 \cdot \overline{x} \\
+ &St_1 \cdot \overline{St_0} \cdot \overline{x} + St_0 \cdot St_1 \cdot \overline{x}
\end{align}
$$
$$

\begin{array}{c c|c}
St_0 & St_1 & Z\\
\hline
0 & 0 & 0\\
0 & 1 & 0\\
1 & 0 & 0\\
1 & 1 & 1\\
\end{array}
\Rightarrow
\begin{align}
Z = St_0 \cdot St_1
\end{align}
$$
che quindi possiamo racchiudere in un circuito tipo
![[circuitoAutomaMoore.png]]
