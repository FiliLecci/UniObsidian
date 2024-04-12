Un componente che prende 2 input (Set e Reset) e restituisce 2 output ($Q$ e $\overline Q$). 
La particolarità di questo circuito è che è in grado di "ricordare" un input anche dopo che esso è stato rimesso a 0.
Se ai valori di input S e R si assegnano rispettivamente 1 e 0, il latch da come output $Q$ e $\overline Q$ rispettivamente 1 e 0. Da qua anche se S tornasse a 0 gli output rimarrebbero invariati.
Al contrario con input 0 e 1 gli output diventano 0 e 1, anche qua impostando nuovamente R a 0 gli output restano invariati.
L'unico problema che si riscontra con questo circuito è se entrambi i valori di input sono 1, in questo caso in una simulazione otteniamo entrambi i valori di output a 0 (che contraddice il fatto che essi sono uno il negato dell'altro) mentre nella realtà ci sono tanti fattori che possono influenzare il risultato, rendendo l'output imprevedibile.
___

![[latchSR.png]]

```tikz
\usepackage{circuitikz}

\begin{document}
\begin{figure}[!ht]
\centering
\resizebox{1\textwidth}{!}{%
\begin{circuitikz}
\tikzstyle{every node}=[font=\Large]
\draw [](10,5.75) to[short] (10,5);
\draw[] (10,5) to[short] (7.25,5);
\draw [](7.25,5) to[short] (7.25,3.5);
\draw [](7.25,3.5) to[short] (7.5,3.5);
\draw [](10,3.25) to[short] (10,4);
\draw[] (10,4) to[short] (7.5,4);
\draw [](7.5,4) to[short] (7.5,5.5);
\draw (7.5,6) to[short] (8,6);
\draw (7.5,5.5) to[short] (8,5.5);
\draw (8,6) node[ieeestd nor port, anchor=in 1, scale=0.89](port){} (port.out) to[short] (10,5.75);
\draw (7.5,3.5) to[short] (8,3.5);
\draw (7.5,3) to[short] (8,3);
\draw (8,3.5) node[ieeestd nor port, anchor=in 1, scale=0.89](port){} (port.out) to[short] (10,3.25);
\draw [](10,5.75) to[short] (10.75,5.75);
\draw [](10,3.25) to[short] (10.75,3.25);
\node [font=\Large] at (11,3.75) {};
\node [font=\Large] at (12.5,4.75) {};
\node [font=\Large] at (11,5.75) {Q};
\draw (10,5.75) to[short, -*] (10,5.75);
\draw (10,3.25) to[short, -*] (10,3.25);
\draw[] (7.5,6) to[short] (6.5,6);
\draw[] (7.5,3) to[short] (6.5,3);
\node [font=\Large] at (6,6) {S};
\node [font=\Large] at (6,3) {R};
\node [font=\Large] at (11.25,3.25) {not Q};
\node [font=\Large] at (11,3.25) {Text};
\end{circuitikz}
}%
\end{document}

\label{fig:my_label}
\end{figure}
```

```verilog
module SR(output q, output notq, input s, input r);

	wire w1, w2;
	wire nw1, nw2;

	or(w1, r, nw2);
	or(w2, s, nw1);

	not(nw1, w1);
	not(nw2, w2);

	assign q=nw1;
	assign notq=nw2;
	
endmodule
```

