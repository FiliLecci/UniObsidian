È composto da due [[D - Latch]], che vengono rispettivamente chiamati *master* e *slave* e che sono collegati nel seguente modo.
![[flipflopD.png]]
Questo particolare collegamento del clock, ha una conseguenza molto importante e cioè che i latch scrivono uno dopo l'altro in intervalli ben precisi (definiti appunto dal clock). Ciò accade perché nel momento in cui il clock è basso viene scritto il latch *master*, quando invece è alto si scrive il latch *slave* che prende come input l'output del *master*.
___
## Write enable (registro)
Il write enable è un segnale che viene usato per "dire" al flip flop quando effettivamente deve scrivere l'input *D*.
È un segnale di 1 bit che per avere l'effetto desiderato basta semplicemente mettere in *AND* con il segnale di clock; così facendo quando il segnale *we* è basso, indipendentemente dal segnale del clock *D* non viene scritto, al contrario se *we* è alto allora la scrittura viene dettata dai tempi scanditi dal clock.
Un flip flop con l'aggiunta di un input *we* si chiama ***registro***.
Unendo $n$ flip flop agli stessi *clock* e *we* ma a input e output differenti possiamo ottenere un registro a $n$ bit.