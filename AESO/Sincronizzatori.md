Nelle reti asincrone possiamo garantire livelli logici corretti facendo passare gli ingressi attraverso dei sincronizzatori.
In mancanza di sincronizzatori si incorre nella possibilità che alcuni ingressi cambino stato allo stesso momento in cui il fronte di salita del clock si presenta, portando quindi ad un valore metastabile (né 0 né 1).

Un sincronizzatore nella maggior parte dei casi risolve questo problema con l'uso di due flip-flop $F1$ e $F2$.
$F1$ campiona l'ingresso $D$ al fronte di salita del clock e restituisce un valore $D2$ che può assumere un valore metastabile. Dopo un po' di tempo, se il ciclo del clock è abbastanza lungo, $D2$ si sarà stabilizzato su un valore e, al fronte di salita successivo del clock, $F2$ campiona $D2$ restituendo un valore stabile.
![[circuitoSincronizzatore.png|300]]
