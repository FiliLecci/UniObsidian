Consideriamo coppie di dati (o dati bivariati) $(x,y)=((x_1,y_1)(x_2,y_2),(...),(x_n,y_n))$ dove $(x_i,y_i)$ è il dato riferito all'i-esimo individuo del campione.

>[!example] Esempio
>In un campione di persone:
>- $x_i$ = temperatura corporea della i-esima persona
>- $y_i$ = pressione della i-esima persona

Serve ad individuare eventuali relazioni tra i dati $x_i$ e $y_i$.
### Grafico di dispersione o scatterplot
Grafico in cui ogni $(x_i,y_i)$ è riportato sul piano cartesiano (come punto con coordinate (x,y))
```tikz
\usepackage{pgfplots}
\begin{document}
\begin{tikzpicture}
\begin{axis}[
    enlargelimits=0.2,
]
    \addplot+ [red, nodes near coords,only marks,
			    mark=x, mark size=4pt,
			    point meta=explicit symbolic]
    table {
        x    y  
        0.5  0.2
        0.2  0.1
        0.7  0.6
        0.35 0.4
        0.65 0.1
    };
\end{axis}
\end{tikzpicture}
\end{document}
```
#### Alcuni esempi
--- start-multi-column: ID_uw4n
```column-settings
Number of Columns: 2
Largest Column: standard
```

```tikz
\usepackage{pgfplots}
\begin{document}
\begin{tikzpicture}
\begin{axis}[
    enlargelimits=0.2,
]
    \addplot+ [red,nodes near coords,only marks,
			    mark=x, mark size=4pt,
			    point meta=explicit symbolic]
    table {
        x    y  
        0.5  0.5
        0.6  1
        0.5  1.6 
        1 0.4
        1.1 0.9
        1.1 1.5
        1.5 0.5
        1.5 1
        1.5 1.5
    };
\end{axis}
\end{tikzpicture}
\end{document}
 ```

--- column-break ---

In questo caso non possiamo dedurre nessun tipo di relazione tra i dati $x_i$ e $y_i$ in quanto dato un $x_i$ non abbiamo modo di stimare un possibile valore di $y_i$

--- end-multi-column
___
--- start-multi-column: ID_2caq
```column-settings
Number of Columns: 2
Largest Column: standard
```

```tikz
\usepackage{pgfplots}
\begin{document}
\begin{tikzpicture}
\begin{axis}[
    enlargelimits=0.2,
]
    \addplot+ [red,nodes near coords,only marks,
			    mark=x, mark size=4pt,
			    point meta=explicit symbolic]
    table {
        x    y  
        0.5 0.5
        0.6 0.7
        0.8 0.6
        0.9 0.9
        1 1.2
        1.2 1.4
        1.5 1.4
        1.6 1.7       
    };
    \addplot[dashed,domain=0:2]{x};
\end{axis}
\end{tikzpicture}
\end{document}
 ```

--- column-break ---

Qui possiamo invece dire che abbiamo una relazione lineare tra i dati; possiamo quindi stimare per un dato $x_i$ il suo valore di $y_i$ seguendo una tendenza lineare.

	--- end-multi-column
___
--- start-multi-column: ID_0a7p
```column-settings
Number of Columns: 2
Largest Column: standard
```

```tikz
\usepackage{pgfplots}
\begin{document}
\begin{tikzpicture}
\begin{axis}[
    enlargelimits=0.2,
]
    \addplot+ [red,nodes near coords,only marks,
			    mark=x, mark size=4pt,
			    point meta=explicit symbolic]
    table {
        x    y  
        0.2 3.8
        0.3 3.5
        0.5 3
		0.5 2.5
		0.6 2.5
		1.1 1.5
		1.1 1
		1 0.6
        2 0
        2.4 0.5
        2.7 0.9
        3.2 1
        3.6 2
        3.7 2.1
        3.8 3.2
        4 3.9
    };
    \addplot[dashed,domain=0:4]{(x-2)^2};
\end{axis}
\end{tikzpicture}
\end{document}
 ```

--- column-break ---

In questo caso possiamo invece notare che c'è ancora una relazione tra i dati ma essa non è lineare. 

--- end-multi-column

