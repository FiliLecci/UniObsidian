Il Latch D è una variante del [[Latch SR]] che utilizza un  [[Clock]] ed un input *D* per definire gli input *S* e *R* ed evitare casi in cui entrambi siano 1.
Questo componente altro non è che un Latch SR con l'aggiunta di un componente che definisce per ogni ciclo del clock gli input *S* e *R* basandosi su *D*.
$$
\begin{array}{c c|c|c}
clock & D & S & R\\
\hline
0 & - & 0 & 0\\
1 & 0 & 1 & 0\\
1 & 1 & 0 & 1
\end{array}
$$
questa tabella di verità può essere riassunta nelle seguenti espressioni
$$
\begin{align}
&S = clock \cdot \overline D\\
&R = clock \cdot D
\end{align}
$$
___
![[latchD.png]]
```verilog
module D(output q, output notq, input clock, input d);
	wire s, r;

	assign r=clock & (~d);
	assign s=clock & d;

	SR sr(q, notq, s, r);
endmodule
```