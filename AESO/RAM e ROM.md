Una RAM (Random Access Memory) è chiamata "random" in quanto il costo di lettura di ogni riga è lo stesso indipendentemente dalla sua locazione.

Questo concetto non vale per le memorie ad accesso sequenziale (un registratore a nastro ad esempio) in quanto il costo di lettura o scrittura di un dato dipende dalla sua posizione (più è lontana la posizione maggiore è il costo).

Esistono due tipi di RAM:
- ***Dinamiche***: I dati sono memorizzati su dei condensatori, è quindi necessario "refreshare" il dato periodicamente e dopo averlo letto altrimenti viene perso;
- ***Statiche***: I dati sono memorizzati usando una coppia di negatori connessi a croce e quindi i bit sono mantenuti finché alimentati.

Una classificazione ancora più generale è quella tra RAM e ROM.
___
## ROM
Le ROM (Read Only Memory) sono memorie di sola lettura.
La principale differenza che le distingue dalle RAM è il fatto che la RAM è una memoria **volatile**, i suoi dati quindi vengono persi una volta spenta, mentre le ROM sono non volativi e quindi mantengono i dati per un tempo indefinito **anche in assenza di alimentazione**.

Le ROM vengono chiamate di sola lettura perché, storicamente, potevano solo essere lette. Ad oggi questa dicitura può risultare ambigua non solo perché le ROM sono esse stesse ad accesso casuale come le RAM, ma soprattutto perché la maggior parte delle ROM moderne possono anche essere sia lette che scritte.
La distinzione maggiore e più importante rimane quindi che le RAM sono volatili mentre le ROM non lo sono.
___
## DRAM
La DRAM (Dynamic RAM) è un tipo di RAM che memorizza i dati come presenza o meno di carica su un condensatore.
Ogni cella di memoria presenta un transistore NMOS che si comporta come un interruttore per connettere o meno il condensatore alla linea di bit.
All'attivazione della linea di parola i transistor dei condensatori si attivano e i bit immagazzinati vengono trasferiti sulle linee di bit.
In caso di lettura i dati vengono trasferiti dai condensatori alle linee di bit, in caso invece di scrittura i dati passano dalle linee di bit ai condensatori.
La lettura è distruttiva in quando per leggere i dati si scaricano i condensatori, per mantenere quindi il dato è necessario effettuare una riscrittura. Riscritture sono anche necessarie ogni pochi millisecondi in quanto le cariche sui condensatori di perdono gradualmente.