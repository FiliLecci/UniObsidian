Notazione
$$
\begin{align*}
\overline{x}\frac{1}{n}\sum^n_{i=1}x_i \quad \text{media camp $x_i$} \quad \sigma(x)\sqrt{Var(x)}\\
\overline{y}\frac{1}{n}\sum^n_{i=1}y_i \quad \text{media camp $y_i$} \quad \sigma(x)\sqrt{Var(y)}
\end{align*}
$$
___
>[!note] Covarianza empirica
>$$Cov_e(x,y) = \frac{1}{n}\sum^n_{i=1}(x_i-\overline x)\cdot(y_i-\overline y)$$
> Ossia la media del prodotto tra tutte le $x$ meno la $x$ media con tutte le $y$ meno la $y$ media.
> >[!example] Esempio
> >Prendiamo come $x$ la temperatura e come $y$ la pressione; la covarianza empirica sarà data dalla media di tutte le temperature $x_i$ meno la temperatura media $\overline x$ moltiplicate con la pressione $y_i$ meno la pressione media $\overline y$. 
> 
> Può essere utile notare che la Covarianza empirica può anche essere definita nel seguente modo
> $$Cov_e(x,y)=\frac{1}{n}\sum^n_{i=1}(x_iy_i)-\overline x \overline y$$

>[!note] Covarianza campionaria
> Come detto per la [[varianza campionaria]], essa è data dalla stessa formula della covarianza empirica solo che invece di $\frac{1}{n}$ usiamo $\frac{1}{n-1}$.
> $$Cov_e(x,y) = \frac{1}{n-1}\sum^n_{i=1}(x_i-\overline x)\cdot(y_i-\overline y)=\frac{n}{n-1}Cov_e(x,y)$$

