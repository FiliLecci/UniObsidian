La seguente rappresentazione grafica:
- si disegna una linea dal minimo $x_{(1)}$ al massimo $x_{(n)}$ dei dati
- si disegna un rettangolo che va dal 1° al 3° quartile, con una linea in corrispondenza del 2° quartile
___
```tikz
\usepackage{pgfplots}
\begin{document}
\begin{tikzpicture}
\begin{axis}
\addplot+ [ boxplot prepared={ lower whisker=5, lower quartile=7, median=8.5, upper quartile=9.5, upper whisker=10, }, ] table [row sep=\\,y index=0] { data\\ 1\\ 3\\ };
\end{axis}
\end{tikzpicture}
\end{document}
```
![[box-plot_example.png]]
